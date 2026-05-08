CLI Router - configuração
<img width="627" height="485" alt="image" src="https://github.com/user-attachments/assets/a06c1d0a-c116-46fb-a8e0-eaa502a7944e" />

Primeiro ping no CMD entre os PCs de mesma rede, dando 100% certo
<img width="410" height="207" alt="image" src="https://github.com/user-attachments/assets/2d56f65e-c030-4337-b0a5-d8522a4f0dcc" />

Ping no CMD entre os PCs de diferentes topologias
O primeiro ping teve 1 falha, ocorrendo 75% de aproveitamento, mas na segunda acabou dando 100%
<img width="451" height="381" alt="image" src="https://github.com/user-attachments/assets/01ad77d0-ea1e-4276-bf41-72e9cc19958c" />

Utilizado 4 PCs (PC0, PC1, PC2, PC3), 2 Switches (2960-24TT Switch0, 2960-24TT Switch 1) e um Roteador (2911 Router2), feito por ligações com cabo normal.


Expandindo a topologia

<img width="1065" height="562" alt="image" src="https://github.com/user-attachments/assets/14592024-3a44-4a46-90ae-60316d5c2f80" />

Usaremos essa tabela de referëncia

<img width="672" height="148" alt="image" src="https://github.com/user-attachments/assets/4ca075ad-828a-4447-9dae-da41cf13037a" />

Configurando os Routers

Router0
<img width="621" height="361" alt="image" src="https://github.com/user-attachments/assets/5c839800-4930-43c1-ae80-3745cfc173a9" />

Router1
<img width="626" height="387" alt="image" src="https://github.com/user-attachments/assets/392fdca7-65ed-4f4c-a2e9-ffda063b6cef" />

Router2
<img width="630" height="410" alt="image" src="https://github.com/user-attachments/assets/d695eea1-7bce-439c-82a0-1b191feea435" />

Para fazermos o roteamento estatico, seguiremos os seguintes passos

Router1 -> Rede C

Primeiro colocamos a rota de IP que queremos no roteador 1, no caso sera o endereco de um dos PCs da rede C

<img width="329" height="28" alt="image" src="https://github.com/user-attachments/assets/eeaa35b9-67eb-4f84-8131-73212ec8f961" />

Depois, no roteador 2, colocamos o endereco de IP que queremos receber, para fazer a troca na comunicacao de dados

<img width="427" height="25" alt="image" src="https://github.com/user-attachments/assets/12d3fc2a-2fc3-41ff-a98a-862984898c9c" />

Depois dessas configuracoes, foi feita a comunicacao de dados entre a topologia B e C, funcionando o teste de ping no CMD, podendo ver o exemplo abaixo

<img width="409" height="235" alt="image" src="https://github.com/user-attachments/assets/4d5e023f-1cbb-4195-af20-70dca3fdcb41" />
<img width="432" height="178" alt="image" src="https://github.com/user-attachments/assets/2da16b7d-58a0-457c-b764-6cdeacc160a9" />

Agora, testaremos o roteamento dinamico. Para isso, precisamos remover os enderecos que colocamos anteriormente do roteamento estatico, utilizando o comando abaixo nos CLIs

<img width="446" height="19" alt="image" src="https://github.com/user-attachments/assets/975f4caa-6150-4b2e-888e-6f81d4256afb" />
<img width="436" height="15" alt="image" src="https://github.com/user-attachments/assets/36a375aa-d435-4521-b3c7-3f787b63e400" />

Agora, teremos que configurar o OSPF em todos os roteadores. 
Para configurar, precisaremos fazer o passo a passo a seguir

Router0
<img width="457" height="108" alt="image" src="https://github.com/user-attachments/assets/f0e3083c-e02b-4079-b3d6-630618ce4c27" />

Router1
<img width="504" height="123" alt="image" src="https://github.com/user-attachments/assets/46498e5d-ca12-473d-bdab-780564a1475b" />

Router2
<img width="637" height="166" alt="image" src="https://github.com/user-attachments/assets/52a600ca-497f-41f4-bd24-438ce40b55f8" />

Depois de configurado, testei o ping novamente e deu certo (R1 -> R2)!
<img width="464" height="200" alt="image" src="https://github.com/user-attachments/assets/248081e8-a55f-4fbb-9b3a-923052dff93c" />

Atualmente, temos essa topologia abaixo. 
<img width="1102" height="564" alt="image" src="https://github.com/user-attachments/assets/e8144891-05a3-4b42-b80e-95b3301a9e27" />

Mas conforme as instrucoes do professor, no final do passo 13, faremos um teste e apagaremos o cabo entre Router1 e Router2 e ver o que acontece

<img width="1071" height="585" alt="image" src="https://github.com/user-attachments/assets/8339bc3f-a3d7-4054-ba9f-d331863e33a4" />

Agora conseguimos entender para que realmente o roteador dinamico serve! Mesmo com uma das rotas apagadas, ele redireciona para que ainda fique funcionando.

<img width="425" height="202" alt="image" src="https://github.com/user-attachments/assets/fef001ec-83cf-432b-8c34-0d97c960f221" />

Nesse caso, como cortamos a conexao entre R1 e R2, eles passaram a se conectar a partir do R0, garantindo ainda uma conexao, mesmo com as conexoes cortadas, excelente!



Isso agora deixa nitido que o dinamico vai se adaptar com diferentes situacoes, ja o estatico, se fizesse esse mesmo rompimento, acabaria cortando a conexao entre R1 e R2 e nao poderiam mais se conectar.





