# Mod 26

Este desafio é baseado na **Cifra de César**, especificamente na variação conhecida como **ROT13**

##### [Link do desafio](https://play.picoctf.org/practice/challenge/144?category=2&page=1)

## Contextualização

A **Cifra de César** é um método de substituição no qual cada letra do texto original é deslocada um número fixo de posições no alfabeto.

O **ROT13** (Rotation 13) é um caso específico dessa cifra, em que o deslocamento é de 13 posições.

Como o alfabeto possui 26 letras, aplicar ROT13 duas vezes retorna ao texto original:

> 13 + 13 = 26 (mod 26)

Por isso o nome do desafio: Mod 26.

## Passo a Passo

Após baixar o arquivo fornecido, obtive a seguinte string codificada: `cvpbPGS{arkg_gvzr_V'yy_gel_2_ebhaqf_bs_ebg13_45559noq}`

A descrição do desafio faz referência direta ao ROT13, indicando que provavelmente essa é a técnica utilizada.

<img width="532" height="182" alt="image" src="https://github.com/user-attachments/assets/2588389e-0a12-45ea-b8ea-478013d686a0" />

Então, usando essa lógica, uso o [site112](https://site112.com/cifra-de-cesar-codificar-descodificar) para decodificar a *flag*

<img width="1215" height="613" alt="image" src="https://github.com/user-attachments/assets/7904d45b-e6de-4dd2-928a-a510b7e58a26" />

## FLAG: picoCTF{next_time_I'll_try_2_rounds_of_rot13_45559abd}

### Conclusão

Este é um excelente desafio introdutório para compreender:

1. Como funcionam cifras de substituição

2. O conceito de deslocamento modular (mod 26)

3. Como identificar padrões simples de criptografia

Apesar de ser um método historicamente importante, a Cifra de César (incluindo ROT13) é considerada insegura atualmente, pois pode ser facilmente quebrada por análise de frequência ou tentativa de todos os deslocamentos possíveis (apenas 25 possibilidades).
