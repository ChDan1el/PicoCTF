Introdução
Esse desafio tem como proposta desvenvolver a busca de informações nos [metadados](https://www.ibm.com/br-pt/think/topics/metadata) de uma imagem, instigando a curiosidade em buscar diferentes métodos e 
ferramentas para o processo.

[Página do desafio](https://play.picoctf.org/practice/challenge/460)

Passo a Passo

1- Inicialmente só temos uma imagem toda vermelha e dicas: duvidar se a imagem está pura e questionar qual é o nome atual do Facebook.

[![red.png](https://i.postimg.cc/8zG5ktD4/red.png)](https://postimg.cc/0btxcGzK)

Refletindo as dicas é possível deduzir que é preciso analisar os metadados da imagem.

2- Existem vários jeitos de analisar metadados, mas neste desafio optei pelo site [Online-Metadata](https://online-metadata.com/pt)

[![Captura-de-tela-2025-09-08-134234.png](https://i.postimg.cc/FzFpQjzH/Captura-de-tela-2025-09-08-134234.png)](https://postimg.cc/G8NGFTvW)


3- Então, através da análise, obtenho um poema:

Crimson heart, vibrant and bold,
Hearts flutter at your sight.
Evenings glow softly red,
Cherries burst with sweet life.
Kisses linger with your warmth,
Love deep as merlot.
Scarlet leaves falling softly,
Bold in every stroke.

Traduzindo:

Coração carmesim, vibrante e ousado.
Corações batem mais rápido ao te ver.
As tardes brilham em vermelho suave.
Cerejas explodem em doce vida.
Beijos permanecem com o teu calor.
Amor profundo como o merlot.
Folhas escarlates caem suavemente.
Ousadia em cada traço.

4- Usando a dica 2 como base, tento recombinar palavras do poema que representam vermelho, como: Crimson heart, Cherries, Kisses, Scarlet.
Mas percebo que esse método não leva a nada. Sendo provavelmente uma distração.

5- Então pesquiso no google métodos de análise de imagem para encontrar arquivos secretos, e descubro a área de [Esteganografia](https://www.kaspersky.com.br/resource-center/definitions/what-is-steganography),
usando as ferramentas citadas no site do [IBSEC](https://ibsec.com.br/10-ferramentas-stegano-uteis-para-ctf/#:~:text=Esteganografia%20%C3%A9%20uma%20t%C3%A9cnica%20de,%2C%20mp3%2C%20wav%2C%20etc.):

5.1- Steghide, [Como usar](https://medium.com/the-kickstarter/steganography-on-kali-using-steghide-7dfd3293f3fa)

Como não sei nenhuma senha fornecida, deixo esse método para depois.

[![Captura-de-tela-2025-09-08-165859.png](https://i.postimg.cc/8C28SdFG/Captura-de-tela-2025-09-08-165859.png)](https://postimg.cc/yJyphZXp)

5.2- zsteg, [Como usar](https://github.com/zed-0xff/zsteg)

Testando o primeiro exemplo depois da instalação, encontro uma string codificada em base64:
cGljb0NURntyM2RfMXNfdGgzX3VsdDFtNHQzX2N1cjNfZjByXzU0ZG4zNTVffQ==

[![Captura-de-tela-2025-09-08-170254.png](https://i.postimg.cc/qgVg66ZH/Captura-de-tela-2025-09-08-170254.png)](https://postimg.cc/0Kn9LjsV)

6- Uso um [decodificador de Base64](https://www.base64decode.org/pt/) e finalmente encontro a flag.

[![Captura-de-tela-2025-09-11-113926.png](https://i.postimg.cc/qMQPtm18/Captura-de-tela-2025-09-11-113926.png)](https://postimg.cc/gnXSQKFJ)

Flag: picoCTF{r3d_1s_th3_ult1m4t3_cur3_f0r_54dn355_}



Conclusão:

Esse desafio foi bem complicado de resolver, pois nos metadados da imagem continha uma distração que me pegou por um tempo.
A questão me fez aprender que existem vários métodos de esconder dados em um arquivo .png, junto com inúmeras ferramentas para poder encontrá-los.












