# Estagio-em-Automacao-em-Python

Problemática:

Em nossa loja, realizamos vendas em real de produtos importados. Entretanto, as últimas variações cambiais têm preocupado a gerência. Para termos maior controle, precisamos ter dados de vendas em dólar e em euro.

[Faturamento_original.xlsx](https://github.com/user-attachments/files/16314866/Faturamento_original.xlsx)

[Faturamento_atualizado.xlsx](https://github.com/user-attachments/files/16314869/Faturamento_atualizado.xlsx)

O ambiente utilizado para a execução deste Teste foi o Compilador Geany.
import pandas as pd.
#Utilizado o Geany para a compilação e execução do teste

# Caminho do arquivo original
original_file_path = 'Faturamento_original.xlsx'
# Caminho do novo arquivo
updated_file_path = 'Faturamento_atualizado.xlsx'

# Carregar o arquivo Excel original
df = pd.read_excel(original_file_path)

# Adicionar novas colunas com as taxas de câmbio fixas
df['Dólar do Dia'] = 5.55  # Taxa fixa retirada às 12:00 em 19/07/2024
df['Euro do Dia'] = 6.05  # Taxa fixa retirada às 12:00 em 19/07/2024

# Calcular faturamento em dólar e euro
df['Faturamento em Dólar'] = df['Faturamento em real'] / df['Dólar do Dia']
df['Faturamento em Euro'] = df['Faturamento em real'] / df['Euro do Dia']

# Limitar os valores a duas casas decimais
df['Dólar do Dia'] = df['Dólar do Dia'].round(2)
df['Euro do Dia'] = df['Euro do Dia'].round(2)
df['Faturamento em Dólar'] = df['Faturamento em Dólar'].round(2)
df['Faturamento em Euro'] = df['Faturamento em Euro'].round(2)

# Salvar as alterações no novo arquivo Excel
df.to_excel(updated_file_path, index=False)

# Print para validação que o Programa foi executado até o final.
print('Arquivo atualizado!')
