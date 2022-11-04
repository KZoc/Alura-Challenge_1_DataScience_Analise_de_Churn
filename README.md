# Alura Challenge 1 de Data Science

## Status: Em Desenvolvimento

## Descrição do Challenge:

Fui foi contratado(a) como cientista de dados pela operadora (fictícia) de telecomunicações Alura Voz. Após a reunião inicial com as pessoas responsáveis pela área de vendas da empresa, foi explicada a importância de se reduzir a Taxa de Evasão de Clientes, conhecido como Churn Rate. Basicamente, o Churn Rate indica o quanto a empresa perdeu de receita ou clientes em um período de tempo.

Como passo inicial sugeri a identificação de clientes que teriam uma maior chance de deixar a empresa. Para isso, é interessante investigar algumas características de clientes ou dos planos de clientes para tentar CLASSIFICAR estas pessoas como potenciais candidatas a deixar a empresa ou não.

Após a solicitação dos dados iniciarei a exploração, tratamento dos dados e modelagem da solução de ML para prever se um cliente irá ou não deixar a empresa.

## Dicionário de Dados:
- customerID: número de identificação único de cada cliente
- Churn: se o cliente deixou ou não a empresa
- gender: gênero (masculino e feminino)
- SeniorCitizen: informação sobre um cliente ter ou não idade igual ou maior que 65 anos
- Partner: se o cliente possui ou não é parceiro ou parceiro
- Dependents: se o cliente possui ou não dependentes
- tenure: meses de contrato do cliente
- PhoneService: assinatura de serviço telefônico
- MultipleLines: assisnatura de mais de uma linha de telefone
- InternetService: assinatura de um provedor internet
- OnlineSecurity: assinatura adicional de segurança online
- OnlineBackup: assinatura adicional de backup online
- DeviceProtection: assinatura adicional de proteção no dispositivo
- TechSupport: assinatura adicional de suporte técnico, menos tempo de espera
- StreamingTV: assinatura de TV a cabo
- StreamingMovies: assinatura de streaming de filmes
- Contract: tipo de contrato
- PaperlessBilling: se o cliente prefere receber online uma fatura
- PaymentMethod: forma de pagamento
- Charges.Monthly: total de todos os serviços do cliente por mês
- Charges.Total: gasto total pelo cliente



## Importando as Bibliotecas Básicas
Para iniciar o projeto decidi começar importando as seguintes bibliotecas:

. Pandas

. Numpy

. Seaborn

. Json

## Iniciando as Análises Exploratórias

 - Ao importar o arquivo json pude visualizar que havia colunas com dados aninhados, portanto, foi necessário fazer a normalização do DF json, para que todas os campos fossem separados corretamente.
 
 Abaixo está o DataFrame com algumas colunas com os dados aninhados:
 
 ![img-01](https://user-images.githubusercontent.com/82530745/187981166-c05dd3a4-647d-4874-959b-9de120d44f4d.png)
 (img-01)
 
 - Abaixo DataFrame normalizado:
 
 ![img-02](https://user-images.githubusercontent.com/82530745/187981444-e3a21591-8b90-4ca4-84f0-90972925ec70.png)
 (img-02)
 
 ### Traduzindo as Colunas
 
 - Uma vez normalizado fiz a tradução das colunas do DataFrame para facilitar o entendimento ao longo das análises. As traduções foram feitas com base no seguinte dicionário:
 
 ![img-03](https://user-images.githubusercontent.com/82530745/187981612-0084be6d-b941-42ef-898f-6bdc08c5bcac.png)
 (img-03)
 
 - Colunas traduzidas
 ![img-04](https://user-images.githubusercontent.com/82530745/199968106-94ffef9c-c58f-407d-9ca2-1eb898c5f7d3.png)
 (img-04)
 
 ### Definindo os Tipos de Variáveis
 
 Para facilitar a análise fiz uma lista com as colunas existentes e que tipo de dado considerei que deveriam ter (img-05), em sequência imprimo quais são os tipos de dados que realmente estão em cada coluna (img-06).

![img-05](https://user-images.githubusercontent.com/82530745/199969908-ecf7eb92-5c9c-4117-a813-9ab30225a214.png)
(img-05)

![img-06](https://user-images.githubusercontent.com/82530745/199969978-085139c7-31eb-4300-bdb1-6b94949d9644.png)
(img-06)

### Verificando e Corrigindo Inconsistências

Para facilitar minhas análises criei um bloco de código que irá retornar um conjundo de dados importantes para cada coluna do dataset.
Com esses dados e a forma como serão mostrados ficará fácil de visualizar se há campos nulos ou vazios, quantos dados tem em cada coluna, quantos dados repetidos tem.

![img-07](https://user-images.githubusercontent.com/82530745/199970471-5aa810cd-58f5-4b21-b12b-d2db0efd540f.png)
(img-07)

![img-08](https://user-images.githubusercontent.com/82530745/199971682-e6e6bb68-102c-42b3-965a-494540ce0a79.png)
(img-08)

#### Após analisar as informações de todas as colunas, fiz algumas observações:


##### <font color=yellow> Cancelamento = Possui 224 células vazias. Vou excluir e guardar em outro dataframe. Também, mudarei YES para 1 e No para 0.</font>
##### <font color=yellow> Gênero = Mudarei Male para 1 e Female para 0.</font>
##### <font color=yellow> Multiplas_Linhas = Verificar se, caso NÃO tenha serviço de telefone o campo aqui não pode ser YES/True.</font>
##### <font color=yellow> Acho importante verificar se não há incoerências entre as respostas das seguintes colunas:</font>
- Segurança_Online
- Serviço_Backup_Online
- Proteção_de_Dispositivo
- Suporte_Técnico
- Assina_TV
- Assina_Filmes
- No caso das colunas acima, se elas tiverem o conteúdo 'No internet service', então é importante conferir se na coluna 'Serviço_de_Internet' ela está com 'No', caso contrário há uma informação conflitante.

##### <font color=yellow> Tipo_de_Contrato = Alterar as células para o seguinte:</font>
- Month_to_month -> 0
- One_year -> 1
- Two_year -> 2
- Assim poderei ordenar essa categoria depois, se for necessário.</font>

##### <font color=yellow> Total_Acumulado = Não têm todas as células preenchidas com números e, também, está como tipo 'object', mas o certo é ser 'float64' por conter apenas números</font>

##### <font color=yellow> Acho interessante criar mais uma coluna com a quantidade de serviços contratados.</font>

### Corrigindo o problema com a coluna Total_Acumulado:

![img-09](https://user-images.githubusercontent.com/82530745/199974158-1095ac35-20f3-4032-ab5a-a71a9e834dee.png)
(img-09)

- Como pode ser visto o problema foi solucionado.

### Checando se não há incoerência entre as colunas Multiplas_Linhas com a coluna Serviço_Telefônico

![img-10](https://user-images.githubusercontent.com/82530745/199975156-664e530b-ef94-478b-b082-73e6026d8282.png)
(img-10)

- A análise acima mostra que está tudo certo.

### Continuando alterações e correções

#### Alterei as células da coluna 'Tipo_de_Contrato' da seguinte forma:
- Month_to_month -> 0
- One year -> 1
- Two year -> 2

#### Depois acrescentei uma nova coluna com o valor do Custo_Diario (item pedido pelo desafio).
- Para isso, usei a coluna de Custo_Mensal_de_Serviços e dividi por 30.

#### Adicionando Coluna 'Serviços_Contratados' na posição 7
- Para fazer isso, primeiro criei uma lista com o nome das colunas que são os serviços disponíveis;
- Utilizando uma combinação de FOR fiz a varredura para cada cliente e criei uma lista com o total de serviços contratados de cada cliente;
- Depois inseri essa lista como uma nova coluna (Serviços_Contratados) na posição 7 no dataframe.

Veja abaixo o conjunto de código para a sequência descrita acima:

![img-11](https://user-images.githubusercontent.com/82530745/199977500-2bc389c1-f43e-4940-aa92-7ff50041a1ad.png)
(img-11)

### Separando os Clientes pelo Churn

- Criei um dataframe só com os casos de CHURN vazio. O nome do dataframe ficou df_Cancelamento_vazio e, também, salvei ele separadamente.

- Depois removi do df principal os clientes com churn vazio.

- Criei um dataframe tipo groupby pela coluna Cancelamento e chamei de df_grupo_status

- Depois separei os clientes que Cancelaram dos que permanecem em dois df, sendo, df_Cancelaram e df_Permanecem.

## Análise Exploratório do grupo dos que Cancelaram

- Fiz duas tabelas cruzadas analisando, dentro do grupo dos que cancelaram, qual a distribuição da idade e de sexo. Uma tabela mostra a quantidade de pessoas e a outra qual a porcentagem dessas quantidades dentro do grupo.

![img-12](https://user-images.githubusercontent.com/82530745/199981265-820f249a-66ac-483b-875c-6f0a2bad77be.png)
(img-12)

