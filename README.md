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

![image](https://github.com/user-attachments/assets/84a508d5-d72e-433f-a5fe-e6fcc6b6b2bb)


##Passo a passo e dificuldades encontradas##
- Não possuia conhecimento da plataforma n8n, fiz pesquisas para entender mais sobre e conversei com amigos e colegas, então podem ter erros.

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
- O código está no My_workflow.json

##Eeveelutions!!!##
-As Eeveelutions representam um caso especial no universo Pokémon, onde uma única espécie (Eevee) pode evoluir para oito formas diferentes. Esta peculiaridade exigiu um tratamento específico no código:

1- Quando o sistema identifica um Eevee (ou detecta múltiplas evoluções), ele ativa um modo especial de processamento. Primeiro, coleta todos os nomes das possíveis evoluções, filtrando variações especiais como as formas Gigantamax. Em seguida, formata essas informações em uma string clara e organizada, listando todas as opções de evolução separadas por vírgulas.
2- Mantém a consistência com o tratamento de outros Pokémon.
3- Fornece informação completa ao usuário final.
4- Permite fácil expansão caso novas Eeveelutions sejam adicionadas.

##Oitavo Passo:
- Depois do código, inserimos um nó para atualizar (update) os dados da planilha, assim preenchendo corretamente as informações criadas.
- Para isso devemos inserir a id da planilha e a página novamente.
- E também é necessário implementar quais colunas devem ser atualizadas.

![image](https://github.com/user-attachments/assets/90bd9b43-7918-44dc-9a68-0de9ae0eb669)

##Resultado final:
- O output do Google Sheets Update deve aparecer a index do Pokémon, seu nome, tipo e sua pré-evolução ou sua próxima evolução.

![image](https://github.com/user-attachments/assets/6ab270a1-5a86-4de5-80e4-e7767a78bbea)

- A estrutura dos nós se encontrará desse jeito:

![image](https://github.com/user-attachments/assets/68bc88b5-d05c-4931-917b-f4316957af1a)


- Caso tudo esteja correto, podemos verificar a planilha do Google Sheets e estará já atualizada com os dados corretos:

![image](https://github.com/user-attachments/assets/e5254806-97c1-4420-8a0f-7737419a4117)


