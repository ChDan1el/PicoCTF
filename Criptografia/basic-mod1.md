# basic-mod1

O desafio consiste em calcular o resto da divisão (operação módulo) de vários números e, em seguida, associar cada resultado a um caractere conforme a tabela
fornecida no enunciado

##### [Link do desafio](https://play.picoctf.org/practice/challenge/253?category=2&page=3)

## Passo a Passo

Ao iniciar o desafio, recebi a seguinte lista de números:

> Lista: 350 63 353 198 114 369 346 184 202 322 94 235 114 110 185 188 225 212 366 374 261 213

O enunciado pede para calcular mod 37 de cada número e converter o resultado para a letra correspondente.

```
Utilizando o 350 como exemplo: 350 mod37

Significa encontrar o resto da divisão de 350 por 37. Sabemos que 

350 = 37 * 9 + 17, logo 350 mod37 = 17
```

Para agilizar o processo, escrevi um programa em C++ que:
1. Lê os números

2. Calcula n % 37

3. Usa o resultado como índice em um vetor com os caracteres correspondentes

```c++
#include <iostream>
using namespace std;

int main(){
    int n;
    char chaves[37] = {
        'A', 'B', 'C', 'D', 'E', 'F', 'G', 'H', 'I', 'J', 'K', 'L', 'M', 
        'N', 'O', 'P', 'Q', 'R', 'S', 'T', 'U', 'V', 'W', 'X', 'Y', 'Z', 
        '0', '1', '2', '3', '4', '5', '6', '7', '8', '9', '_'
    };
    
    cin >> n;
    
    while(n!=0){
	cout<<chaves[n%37];
	cin>>n;	
	}
    return 0;
}
```

Entrada utilizada: 350 63 353 198 114 369 346 184 202 322 94 235 114 110 185 188 225 212 366 374 261 213 0

> o 0 é para encerrar o programa

Saída obtida: R0UND_N_R0UND_ADD17EC2

## FLAG: picoCTF{R0UND_N_R0UND_ADD17EC2}

### Conclusão

Este desafio é excelente para reforçar o entendimento da operação módulo e sua aplicação prática em sistemas de codificação.

Além disso, ele introduz conceitos fundamentais da aritmética modular, que são amplamente utilizados em criptografia moderna, incluindo algoritmos mais avançados que utilizam propriedades matemáticas semelhantes.
