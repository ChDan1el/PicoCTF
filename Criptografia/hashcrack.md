# hashcrack

Este desafio consiste em quebrar hashes utilizando uma ferramenta de sua escolha

##### [Link do desafio](https://play.picoctf.org/practice/challenge/475?category=2&page=1)

## Contextualização
Hash é uma função criptográfica unidirecional que gera uma string de tamanho fixo, variando de acordo com o algoritmo utilizado, como **MD5**, **SHA-1** e **SHA-256**

Ela é comumente utilizada para:

Armazenamento seguro de senhas em sistemas

Verificação de integridade de dados durante transmissões

Por ser unidirecional, não é possível "descriptografar" um hash diretamente. O que fazemos é tentar descobrir a entrada original por meio de técnicas como força bruta, dicionário ou consulta a bases de dados públicas.

## Passo a Passo

Ao iniciar o desafio, é solicitada uma conexão via netcat com o servidor. Para isso, utilizei o próprio shell disponibilizado pelo picoCTF.

<img width="565" height="166" alt="image" src="https://github.com/user-attachments/assets/5dd12c6c-a9f4-4a78-9ff5-8a1ead1cd5b3" />

Após a conexão, o primeiro hash fornecido foi: `482c811da5d5b4bc6d497ffa98491e38`

#### Para quebrá-lo, utilizei o site [CrackStation](https://crackstation.net/), que consulta grandes bases de dados de hashes já previamente calculados

Ao inserir o hash no site, foi retornada: A senha correspondente e o algoritmo utilizado

<img width="1286" height="123" alt="image" src="https://github.com/user-attachments/assets/e6a16d31-f99f-4346-b482-0a293808d35e" />

Após inserir a senha no desafio, o servidor solicitou a quebra de um novo hash: `b7a875fc1ea228b9061041b7cec4bd3c52ab3ce3`

<img width="698" height="179" alt="Captura de tela 2026-02-17 141957" src="https://github.com/user-attachments/assets/99a8bffe-2e55-4073-9139-2c1319798603" />

Utilizando novamente a mesma ferramenta, obtive a senha correspondente.

<img width="1252" height="69" alt="image" src="https://github.com/user-attachments/assets/4300e1cc-9889-4543-adbe-bb208c268c83" />

Em seguida, o desafio forneceu um terceiro e último hash: `916e8c4f79b25028c9e467f1eb8eee6d6bbdff965f9928310ad30a8d88697745`

<img width="700" height="243" alt="image" src="https://github.com/user-attachments/assets/bec958de-5c5f-49c5-8e58-ff62e0391e69" />

Aplicando o mesmo procedimento, consegui identificar a senha correta.

<img width="1266" height="79" alt="image" src="https://github.com/user-attachments/assets/8c26f102-05d0-4537-bbe2-6ebbea5259d7" />

Por fim, ao inserir a última resposta, o servidor retornou a *flag* do desafio.

<img width="704" height="306" alt="image" src="https://github.com/user-attachments/assets/f7eca77c-535e-4fa0-8a1e-f69bfad16545" />

## FLAG: picoCTF{UseStr0nG_h@shEs_&PaSswDs!_6965e43b}








