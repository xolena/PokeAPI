# Automação Pokémon com n8n e PokéAPI

## Objetivo
Automatizar o preenchimento de planilhas com dados de Pokémon usando:
- n8n (ETL/automação)
- PokéAPI (fonte de dados)
- Google Sheets (saída)

## Como Executar
1. Importe o `n8n_workflow.json` no seu n8n
2. Configure as credenciais do Google Sheets
3. Execute o fluxo manualmente

## Resultados Esperados
Planilha com:
- Nome do Pokémon capitalizado
- Tipos concatenados
- Cadeia evolutiva

![image](https://github.com/user-attachments/assets/e5254806-97c1-4420-8a0f-7737419a4117)

##Passo a passo e dificuldades encontradas
- Não possuia conhecimento da plataforma n8n, então fiz pesquisas para entender mais sobre.

Primeiro passo:
- Configurar o n8n e o NodeJs.
- Fazer as credenciais do Google Sheets com a planilha e o número dos Pokémons.

![image](https://github.com/user-attachments/assets/ad4a45d4-1454-4fbc-9231-a5c708d27c29)

Segundo Passo: 
- Após as credenciais registradas já é possível criar os nós.
- Criar um nó Trigger que serve para iniciar a automação e atualiza automaticamente os dados dos pokémon quando a planilha muda elimina a necessidade de executar manualmente o fluxo.

![image](https://github.com/user-attachments/assets/12447fa1-ba8d-4dff-84eb-c68193b071c1)

Terceiro Passo:
- Após o Trigger que começa a nossa automação, é preciso inserir um nó que puxe os dados da planilha.
- Criar um Nó com o Google Sheets com o id da planilha e sua respectiva página.

![image](https://github.com/user-attachments/assets/5eb65c2a-a7fb-441e-8ca5-9c852e269834)

Quarto Passo:
- Agora com a planilha inserida, precisamos inserir a PokeAPI para que possa ler os dados de a cordo com a index de cada pokemon e também filtrando


