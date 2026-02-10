# Super Serial
Este é um desafio de exploração web, tendo o foco em PHP, serialização e cookies.

##### [Link do desafio](https://play.picoctf.org/practice/challenge/180?page=1&search=super%20serial)

## Passo a passo

Ao iniciar o desafio me deparo com uma simples página de login, logo já testando *username: admin* e *password: admin*

<img width="687" height="466" alt="image" src="https://github.com/user-attachments/assets/de78160c-eac3-41b1-b28d-254c671c71ff" />

Não funcionou, se não seria muito fácil de resolver. Mas, fui redirecionado para uma página index.php

<img width="939" height="167" alt="image" src="https://github.com/user-attachments/assets/a335f331-3d65-4031-ac77-231c568c9eff" />

Depois disso testo rotas na URL, como /admin, /dashboard, conseguindo achar algo em /robots.txt

<img width="553" height="133" alt="image" src="https://github.com/user-attachments/assets/f511b87f-f1bd-4c88-83ee-59da51f1e005" />

Aqui tem uma página não indexada ao dominio, colocando na URL não chega a lugar nenhum

<img width="594" height="211" alt="image" src="https://github.com/user-attachments/assets/361a3695-2243-4f55-81b4-508989d9d65b" />

No texto da aba da página robots.txt o nome do arquivo termina me phps, sendo uma forma de compartilhar o código php, não havendo execuxão do mesmo. Logo, testo phps na página do index.php

<img width="920" height="298" alt="image" src="https://github.com/user-attachments/assets/6014f6e7-9111-45ea-b01f-0d8a8fadf367" />

Então aqui que começa o verdadeiro desafio. Nessa parte do código é referenciado outra duas partes, o authentication.php e cookie.php

Como é processado a autenticação

<img width="604" height="552" alt="image" src="https://github.com/user-attachments/assets/42142c34-a48c-4402-8e5c-5db17156ab1c" />

Como é processado o cookie

<img width="676" height="864" alt="image" src="https://github.com/user-attachments/assets/dc8cbadd-ba2c-47cc-8155-6ff71d5ef11e" />






