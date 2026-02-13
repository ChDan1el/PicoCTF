Introdução

Este é um excecelnte desafio para iniciantes em decodificação, ele se baseia em dar uma string codificada e transformá-la na flag.
São usados dois tipos de codificação: [base64](https://pt.wikipedia.org/wiki/Base64) e [cifra de César](https://pt.wikipedia.org/wiki/Cifra_de_C%C3%A9sar)

[Página do desafio](https://play.picoctf.org/practice/challenge/418)

Passo a Passo

1- Depois de baixar o arquivo, identifico que a string está codificada em Base64, pois termina com "==":
d3BqdkpBTXtqaGx6aHlfazNqeTl3YTNrX2g0N2o2azY5fQ==

2- Pegando essa string e jogando em um decodificador, é retornada outra string codificada:
wpjvJAM{jhlzhy_k3jy9wa3k_h47j6k69}

[![Captura-de-tela-2025-09-08-175743.png](https://i.postimg.cc/tT199HPM/Captura-de-tela-2025-09-08-175743.png)](https://postimg.cc/qhdPGS1s)

3- Tomando como dica a tag do desafio no site, pego a string retornada e coloco em um [decodificador de cifra de cesar](https://site112.com/cifra-de-cesar-codificar-descodificar).

Fazendo uma conta básica para encontrar o número de deslocamento, comparo o "J" maiúsculo da string com o "C" maiúsculo do início padrão das flags do site [picoCTF](https://play.picoctf.org/),picoCTF{...}, sendo o C=3 e J=10,
seguindo a numeração da ordem alfabética, fica 10-3=7, logo o deslocamento é de 7 letras para a direita.

[![Captura-de-tela-2025-09-08-181601.png](https://i.postimg.cc/L8NSfs3W/Captura-de-tela-2025-09-08-181601.png)](https://postimg.cc/QF9vZhPg)

4- Retornando a flag.


Flag: picoCTF{caesar_d3cr9pt3d_a47c6d69}



Conclusão:

Esse foi um desafio simples de decodificação, precisando decodificar somente duas vezes para encontrar a flag certa.
Ele foi excelente para encontrar padrões de codificação de Base64 e cifra de César.






