# The Numbers

> Dica: The flag is in the format PICOCTF{}

##### [Link do desafio](https://play.picoctf.org/practice/challenge/68?category=2&page=1)

## Passo a Passo

Ao baixar a imagem fornecida pelo desafio, é possível visualizar uma sequência de números organizada em dois grupos]

Esses números aparentemente representam algum tipo de codificação da flag

<img width="387" height="217" alt="the_numbers" src="https://github.com/user-attachments/assets/8a7825df-a379-4e0e-8d4c-e5652d3f3c86" />

A primeira ideia que me veio à cabeça foi que cada número poderia corresponder à sua posição no alfabeto, como: **A=1, B=2, C=3, etc**.
Essa hipótese faz sentido,pois o número 3 aparece duas vezes, o que poderia indicar a letra C, compatível com o formato `PICOCTF{}` fornecido na dica.

<img width="420" height="92" alt="image" src="https://github.com/user-attachments/assets/45f1cbfa-16e5-4f43-930b-c6e20afc61f4" />

Seguindo essa lógica, basta substituir cada número pela letra correspondente à sua posição no alfabeto

<img width="1530" height="149" alt="image" src="https://github.com/user-attachments/assets/19ede4bb-d76d-44aa-80cb-2decdafcfa62" />

Aplicando essa conversão a toda a sequência numérica da imagem, obtemos a *flag*

## FLAG: PICOCTF{THENUMBERSMASON}

### Conclusão

Este é um ótimo desafio introdutório de criptografia. Apesar de ser bastante simples, ele demonstra como uma mensagem, após ser codificada, pode se tornar ilegível.

Assim, apenas quem conhece o método de decodificação (ou a “chave”) consegue acessar o conteúdo original.
