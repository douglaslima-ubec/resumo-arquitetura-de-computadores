#IEEE 754

Padrão de representação de números do tipo ponto flutuante em binário.

#Float
Ponto flutuante de precisão simples com tamanho de 32 bits e precisão de 23 bits.

#Double
Ponto flutuante de precisão dupla com tamanho de 64 bits e precisão de 53 bits.

#Double extended
Ponto flutuante de precisão dupla com tamanho de 80 bits e precisão de 63 bits.

#Fórmula
(-1)^S x M x 2^E
- S: bit de sinal 0 (positivo) e 1 (negativo)
- M: mantissa, valor fracionário no intervalo [1.0, 2.0)
- E: expoente

#Codificação
S | Exp[^1] | Frac[^2]
[^1]: Codifica o expoente
[^2]: Codifica a mantissa

#Tamanho em bits
##Float
| S | Exp     | Frac    |
| - | ------- | ------- |
| 1 | 8 bits  | 23 bits |
| - | ------- | ------- |
##Double
| S | Exp     | Frac    |
| - | ------- | ------- |
| 1 | 11 bits | 53 bits |
| - | ------- | ------- |

#Cálculos
- 1. Converter o número em binário
	- 1.1. A parte fracionária pode ser convertida multiplicando ela por 2 e subtraindo a parte mais significativa sucetivas vezes.
- 2. Obter a mantissa **normalizada** movendo a vírgula até o número ficar no intervalo [1.0, 2.0)
	- 2.1. Transformar o número em notação de base 2 elevado a quantidade de casas que a vírgula "pulou"
- 3. Calcular o expoente pela fórmula: E = exp + bias
	- 3.1. O valor de exp será negativo se o expoente for negativo
- 4. Subtrair a parte fracionária da mantissa
- 5. Converter o expoente em binário de 8 bits (float) ou 11 bits (double)
- 6. Agrupar os bits de acordo com a codificação IEEE 754
