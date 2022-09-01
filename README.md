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
