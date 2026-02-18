# interencdec

Este é um excecelnte desafio para iniciantes em decodificação, ele se baseia em dar uma string codificada e transformá-la na flag.
São usados dois tipos de codificação: [base64](https://pt.wikipedia.org/wiki/Base64) e [cifra de César](https://pt.wikipedia.org/wiki/Cifra_de_C%C3%A9sar)

> Dica: Engaging in various decoding processes is of utmost importance

##### [Link do desafio](https://play.picoctf.org/practice/challenge/418)

## Passo a Passo

1- Depois de baixar o arquivo, identifico que a string está codificada em Base64, pois termina com "==":
`d3BqdkpBTXtqaGx6aHlfazNqeTl3YTNrX2g0N2o2azY5fQ==`

2- Pegando essa string e jogando em no [Cyberchef](https://gchq.github.io/CyberChef/), é retornada outra string codificada em base64:
`b'd3BqdkpBTXtqaGx6aHlfazNqeTl3YTNrX2g0N2o2azY5fQ=='`

<img width="1312" height="507" alt="image" src="https://github.com/user-attachments/assets/5311ee41-8214-4881-89b8-cd97e0fb36ef" />

3- Pegando somente oque está entre aspas simpes, decodifico novamente a string, retornando `wpjvJAM{jhlzhy_k3jy9wa3k_h47j6k69}`

<img width="1131" height="531" alt="image" src="https://github.com/user-attachments/assets/82443423-968d-415e-8042-abb93cf9dcf0" />

4- Tomando como dica a tag do desafio no site, pego a string retornada e coloco em um [decodificador de cifra de cesar](https://site112.com/cifra-de-cesar-codificar-descodificar).

Fazendo uma conta básica para encontrar o número de deslocamento, comparo o "J" maiúsculo da string com o "C" maiúsculo do início padrão das flags do site [picoCTF](https://play.picoctf.org/),picoCTF{...}, sendo o C=3 e J=10,
seguindo a numeração da ordem alfabética, fica 10-3=7, logo o deslocamento é de 7 letras para a direita

[![Captura-de-tela-2025-09-08-181601.png](https://i.postimg.cc/L8NSfs3W/Captura-de-tela-2025-09-08-181601.png)](https://postimg.cc/QF9vZhPg)

5- Retornando a *flag*

## Flag: picoCTF{caesar_d3cr9pt3d_a47c6d69}

#### Conclusão:

Esse foi um desafio simples de decodificação, precisando decodificar somente duas vezes para encontrar a flag certa.
Ele foi excelente para encontrar padrões de codificação de Base64 e cifra de César.








