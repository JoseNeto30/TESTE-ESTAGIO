# TESTE-ESTAGIO
TESTE PARA ESTAGIO -TARGET SISTEMAS - SP

Técnica:

1) Observe o trecho de código abaixo: int INDICE = 13, SOMA = 0, K = 0;
Enquanto K < INDICE faça { K = K + 1; SOMA = SOMA + K; }
Imprimir(SOMA);
Ao final do processamento, qual será o valor da variável SOMA?

2) Dado a sequência de Fibonacci, onde se inicia por 0 e 1 e o próximo valor sempre será a soma dos 2 valores anteriores (exemplo: 0, 1, 1, 2, 3, 5, 8, 13, 21, 34...), escreva um programa na linguagem que desejar onde, informado um número, ele calcule a sequência de Fibonacci e retorne uma mensagem avisando se o número informado pertence ou não a sequência.

IMPORTANTE: Esse número pode ser informado através de qualquer entrada de sua preferência ou pode ser previamente definido no código;

3) Dado um vetor que guarda o valor de faturamento diário de uma distribuidora, faça um programa, na linguagem que desejar, que calcule e retorne:
• O menor valor de faturamento ocorrido em um dia do mês;
• O maior valor de faturamento ocorrido em um dia do mês;
• Número de dias no mês em que o valor de faturamento diário foi superior à média mensal.

IMPORTANTE:
a) Usar o json ou xml disponível como fonte dos dados do faturamento mensal;
b) Podem existir dias sem faturamento, como nos finais de semana e feriados. Estes dias devem ser ignorados no cálculo da média;

4) Dado o valor de faturamento mensal de uma distribuidora, detalhado por estado:
• SP – R$67.836,43
• RJ – R$36.678,66
• MG – R$29.229,88
• ES – R$27.165,48
• Outros – R$19.849,53

Escreva um programa na linguagem que desejar onde calcule o percentual de representação que cada estado teve dentro do valor total mensal da distribuidora.  

5) Escreva um programa que inverta os caracteres de um string.

IMPORTANTE:
a) Essa string pode ser informada através de qualquer entrada de sua preferência ou pode ser previamente definida no código;
b) Evite usar funções prontas, como, por exemplo, reverse;


###   RESOLUÇÃO DO TESTE ABAIXO ###
import json
1) Soma de K até INDICE
def calcular_soma():
    INDICE = 13
    SOMA = 0
    K = 0
    while K < INDICE:
        K = K + 1
        SOMA = SOMA + K
    print(f"1) Valor da variável SOMA: {SOMA}\n")

2) Verificação de número na sequência de Fibonacci
def fibonacci(n):
    a, b = 0, 1
    while a <= n:
        if a == n:
            return True
        a, b = b, a + b
    return False

def verificar_fibonacci():
    numero = int(input("2) Informe um número para verificar se pertence à sequência de Fibonacci: "))
    if fibonacci(numero):
        print(f"O número {numero} pertence à sequência de Fibonacci.\n")
    else:
        print(f"O número {numero} não pertence à sequência de Fibonacci.\n")

3) Cálculo do faturamento diário
def calcular_faturamento_diario():
    faturamento = '''
    {
        "faturamento_diario": [0, 1500, 2500, 3000, 0, 1800, 0, 2200, 2700, 0, 1900, 3000, 0, 1500, 3200, 0, 0, 2800, 2600, 0, 2900, 3300, 0, 2100, 2000, 0, 0, 2400, 3100, 0]
    }
    '''
    dados = json.loads(faturamento)
    faturamento_diario = dados['faturamento_diario']

    # Remover dias sem faturamento
    faturamento_diario = [x for x in faturamento_diario if x > 0]

    menor_faturamento = min(faturamento_diario)
    maior_faturamento = max(faturamento_diario)
    media_mensal = sum(faturamento_diario) / len(faturamento_diario)

    dias_acima_media = sum(1 for x in faturamento_diario if x > media_mensal)

    print(f"3) Menor faturamento: {menor_faturamento}")
    print(f"   Maior faturamento: {maior_faturamento}")
    print(f"   Dias com faturamento acima da média: {dias_acima_media}\n")

4) Percentual de faturamento por estado
def calcular_percentual_faturamento():
    faturamento_por_estado = {
        "SP": 67836.43,
        "RJ": 36678.66,
        "MG": 29229.88,
        "ES": 27165.48,
        "Outros": 19849.53
    }

    faturamento_total = sum(faturamento_por_estado.values())

    print("4) Percentual de faturamento por estado:")
    for estado, valor in faturamento_por_estado.items():
        percentual = (valor / faturamento_total) * 100
        print(f"   {estado}: {percentual:.2f}%")
    print("")

5) Inversão de uma string
def inverte_string(s):
    invertida = ""
    for char in s:
        invertida = char + invertida
    return invertida

def inverter_string():
    texto = input("5) Digite uma string para ser invertida: ")
    print(f"   String invertida: {inverte_string(texto)}\n")

Chamada das funções
def main():
    calcular_soma()
    verificar_fibonacci()
    calcular_faturamento_diario()
    calcular_percentual_faturamento()
    inverter_string()

if __name__ == "__main__":
    main()




