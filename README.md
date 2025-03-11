# 1) Cálculo do valor final da variável SOMA
INDICE = 13
SOMA = 0
K = 0

while K < INDICE:
    K = K + 1
    SOMA = SOMA + K

print("Valor final de SOMA:", SOMA)

# 2) Verifica se um número pertence à sequência de Fibonacci
def pertence_fibonacci(n):
    if n < 0:
        return False
    a, b = 0, 1
    while b < n:
        a, b = b, a + b
    return b == n or a == n

try:
    num = int(input("Digite um número para verificar se pertence à sequência de Fibonacci: "))
    if pertence_fibonacci(num):
        print(f"O número {num} pertence à sequência de Fibonacci.")
    else:
        print(f"O número {num} NÃO pertence à sequência de Fibonacci.")
except ValueError:
    print("Entrada inválida. Digite um número inteiro.")

# 3) Cálculo de estatísticas de faturamento diário
import json

try:
    json_input = input("Digite o JSON com o faturamento diário: ")
    if not json_input.strip():
        raise ValueError("Nenhum dado fornecido.")
    
    dados_faturamento = json.loads(json_input)
    if not isinstance(dados_faturamento, list):
        raise ValueError("O JSON deve ser uma lista de objetos.")
    
    valores = [dia.get("valor", 0) for dia in dados_faturamento if isinstance(dia.get("valor"), (int, float)) and dia["valor"] > 0]
    
    if valores:
        menor = min(valores)
        maior = max(valores)
        media = sum(valores) / len(valores)
        dias_acima_media = sum(1 for v in valores if v > media)
        
        print(f"Menor faturamento: {menor}")
        print(f"Maior faturamento: {maior}")
        print(f"Dias com faturamento acima da média: {dias_acima_media}")
    else:
        print("Nenhum faturamento registrado.")
except (ValueError, json.JSONDecodeError) as e:
    print(f"Erro ao processar os dados: {e}")

# 4) Cálculo do percentual de faturamento por estado
faturamento_estados = {
    "SP": 67836.43,
    "RJ": 36678.66,
    "MG": 29229.88,
    "ES": 27165.48,
    "Outros": 19849.53,
}

total = sum(faturamento_estados.values())

if total > 0:
    for estado, valor in faturamento_estados.items():
        percentual = (valor / total) * 100
        print(f"{estado}: {percentual:.2f}%")
else:
    print("Faturamento total é zero, não é possível calcular percentuais.")

# 5) Inverter uma string sem usar funções prontas
def inverter_string(s):
    invertida = ""
    for char in reversed(s):
        invertida += char
    return invertida

string = input("Digite uma string para inverter: ")
print("String invertida:", inverter_string(string))
