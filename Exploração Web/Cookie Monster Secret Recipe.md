Introdução

Este é um desafio para iniciantes sobre exploração de websites, retirado do site [picoCTF](https://play.picoctf.org).

[Página do desafio](https://play.picoctf.org/practice/challenge/469)

O enunciado gira em torno da análise da ferramenta de inspeção de páginas, com foco na 
funcionalidade dos [cookies](https://www.kaspersky.com.br/resource-center/definitions/cookies)

Passo a passo da resolução

1- Ao entrar no site, nos deparamos apenas com uma página de login. O mais lógico é 
inspecionar o código da página, mas nada de relevante é encontrado.

[![Captura-de-tela-2025-09-08-131300.png](https://i.postimg.cc/yYXYkcLT/Captura-de-tela-2025-09-08-131300.png)](https://postimg.cc/mtkGnzfc)


2- Uma tentativa comum é verificar o arquivo /robots.txt,adicionando /robots.txt no final do 
URL ,mas neste caso só existe uma mensagem indicando o caminho correto do site
[![Captura-de-tela-2025-09-08-131759.png](https://i.postimg.cc/fTwQqFvx/Captura-de-tela-2025-09-08-131759.png)](https://postimg.cc/rzYHKf3m)

3- Seguindo a dica 2 do desafio, decidi verificar os cookies do site. Como só existem 
cookies depois de interagir com o site, realizei um login qualquer.

4- Após a tentativa de login, sou direcionado para outra página que informa que o login 
falhou. Junto com a mensagem de falha de login também há outra dica relacionado aos cookies,
confirmando minha hipótese de que os cookies conteriam alguma informação útil.

[![Captura-de-tela-2025-09-08-131908.png](https://i.postimg.cc/C1H6jhX9/Captura-de-tela-2025-09-08-131908.png)](https://postimg.cc/N9F4tcgx)

5- Voltando à página principal e inspecionando os cookies, encontro uma linha chamada 
secret_recipe com uma mensagem codificada em base64:
cGljb0NURntjMDBrMWVfbTBuc3Rlcl9sMHZlc19jMDBraWVzX0IzQUQ5NEMyfQ%3D%3D
[![Captura-de-tela-2025-09-08-132053.png](https://i.postimg.cc/tCmvdmvR/Captura-de-tela-2025-09-08-132053.png)](https://postimg.cc/rKx9MgL7)


6- Decodificando a string  no site [cyberchef](https://gchq.github.io/CyberChef/) obtenho a
flag!
[![Captura-de-tela-2025-09-11-113814.png](https://i.postimg.cc/htDK6z50/Captura-de-tela-2025-09-11-113814.png)](https://postimg.cc/0b4gJQx6)


Flag: picoCTF{c00k1e_m0nster_l0ves_c00kies_B3AD94C2}


Conclusão:

Esse desafio é fácil e ao mesmo tempo excelente para o aprendizado, pois nos é ensinado a 
funcionalidade do tão falado cookie de site, desenvolvendo a lógica em gravar dados nos 
cookies e como podemos extrair informações valiosas a partir deles, neste caso, a flag 
codificada.
