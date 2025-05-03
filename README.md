# Automação Pokémon com n8n e PokéAPI

## Objetivo
Automatizar o preenchimento de planilhas com dados de Pokémon usando:
- n8n (ETL/automação)
- PokéAPI (fonte de dados)
- Google Sheets (saída)

## Como Executar
1. Importe o `n8n_workflow.json` no seu n8n.
2. Configure as credenciais do Google Sheets.
3. Execute o fluxo manualmente.

## Resultados Esperados
Planilha com:
- Nome do Pokémon capitalizado.
- Tipos concatenados.
- Cadeia evolutiva.

![image](https://github.com/user-attachments/assets/e5254806-97c1-4420-8a0f-7737419a4117)

##Passo a passo e dificuldades encontradas##
- Não possuia conhecimento da plataforma n8n, então fiz pesquisas para entender mais sobre.

##Primeiro passo:
- Configurar o n8n e o NodeJs.
- Fazer as credenciais do Google Sheets com a planilha e o número dos Pokémons.

![image](https://github.com/user-attachments/assets/ad4a45d4-1454-4fbc-9231-a5c708d27c29)

##Segundo Passo: 
- Após as credenciais registradas já é possível criar os nós.
- Criar um nó Trigger que serve para iniciar a automação e atualiza automaticamente os dados dos pokémon quando a planilha muda elimina a necessidade de executar manualmente o fluxo.

![image](https://github.com/user-attachments/assets/12447fa1-ba8d-4dff-84eb-c68193b071c1)

##Terceiro Passo:
- Após o Trigger que começa a nossa automação, é preciso inserir um nó que puxe os dados da planilha.
- Criar um Nó com o Google Sheets com o id da planilha e sua respectiva página.

![image](https://github.com/user-attachments/assets/5eb65c2a-a7fb-441e-8ca5-9c852e269834)

##Quarto Passo:
- Agora com a planilha inserida, precisamos inserir a PokeAPI para que possa ler os dados de acordo com a index de cada Pokémon.
- Devemos inserir um nó de HTTP REQUEST(nomeei como HTTP REQUEST1), com o link da API.

 ![image](https://github.com/user-attachments/assets/5530f5ff-6966-4db2-a969-397cc6ee1292)

*Através do código, iremos filtrar dos dados da PokeAPI, como seu número id, nome e tipos.

##Quinto Passo:
- Agora precisamos do segundo HTTP REQUEST(nomeei como HTTP REQUEST2), onde puxa as linhas evolutivas de cada linha da planilha.

![image](https://github.com/user-attachments/assets/6db10684-7b8a-452b-bae2-ecde4bf2574c)

##Sexto Passo:
- Para que os dados da cadeia evolutiva sejam corretos, precisamos de um terceiro HTTP REQUEST(nomeei como HTTP REQUEST3).
- Com esse terceiro HTTP REQUEST, podemos verificar os dados e filtrar as linhas evolutivas de cada Pokémon.

![image](https://github.com/user-attachments/assets/3bad0ca3-f318-4751-8382-4f7544135a2b)

##Sétimo Passo:
- Com os 3 HTTP's, podemos inserir o nó de função, ou seja o código.
- O código vai filtrar todos os dados necessários, nome, tipo e linha evolutiva.
- Segue o código:




