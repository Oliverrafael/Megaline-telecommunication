# Descrição do projeto
Você trabalha como analista para a empresa de telecomunicações Megaline. A empresa oferece aos clientes dois planos pré-pagos: Surf e Ultimate. O departamento comercial quer saber qual dos planos gera mais receita para ajustar o orçamento de publicidade.

# Objetivo do projeto
Você vai realizar uma análise preliminar dos planos com base em uma pequena seleção de clientes. Você terá dados de 500 clientes da Megaline: que clientes são, de onde eles são, qual plano usam e o número de chamadas e mensagens realizadas em 2018. Seu trabalho é analisar o comportamento dos clientes e determinar qual plano pré-pago gera mais receita. Mais tarde, nas instruções do projeto, você verá exatamente quais aspectos do comportamento dos clientes precisa analisar. Determinar qual plano, em média, gera mais receita é uma tarefa que pode ser resolvida usando testes estatísticos. Você vai receber mais informação sobre isso na seção de instruções do projeto.

## Datasets
- megaline_calls.csv
- megaline_internet.csv
- megaline_messages.csv
- megaline_plans.csv
- megaline_users.csv

## Descrição dos planos
Observação: a Megaline arredonda segundos para minutos e megabytes para gigabytes. Para chamadas, cada chamada individual é arredondada para cima: mesmo que uma chamada tenha durado apenas um segundo, um minuto será contado. Para tráfego da web, sessões individuais da web não são arredondadas para cima. Ao invés disso, o total do mês é arredondado para cima. Se alguém usar 1.025 megabytes no mês, a cobrança será de 2 gigabytes.

Aqui está uma descrição dos planos:

Surf

Preço mensal: 20,00
500 minutos mensais, 50 mensagens de texto e 15 GB de dados
Após exceder os limites do pacote:
1 minuto: 3 centavos
1 mensagem de texto: 3 centavos
1 GB de dados: $10
Ultimate

Preço mensal: 70,00
3.000 minutos mensais, 1.000 mensagens de texto e 30 GB de dados
Após exceder os limites do pacote:
1 minuto: 1 centavo
1 mensagem de texto: 1 centavo
1 GB de dados: $7

## Dicionario dos dados
- A tabela users (dados sobre usuários):
 
    - user_id — identificador exclusivo do usuário
    - first_name — nome do usuário
    - last_name — sobrenome do usuário
    - age — idade do usuário (em anos)
    - reg_date — data da inscrição (dd, mm, aa)
    - churn_date — a data que o usuário parou de usar o serviço (se o valor estiver ausente, isso significa que o plano estava em uso quando o banco de dados foi extraído)
    - city — cidade de residência do usuário
    - plan — nome do plano

- A tabela calls (dados sobre as chamadas):
 
    - id — identificador de chamada exclusivo
    - call_date — data da chamada
    - duration — duração da chamada (em minutos)
    - user_id — identificador do usuário que faz a chamada

- A tabela messages (dados sobre mensagens de texto):
 
    - id — identificador exclusivo da mensagem de texto
    - message_date — data da mensagem de texto
    - user_id — identificador do usuário que envia a mensagem de texto

- A tabela internet (dados sobre sessões web):
 
    - id — identificador exclusivo da sessão
    - mb_used — volume de dados gasto durante a sessão (em megabytes)
    - session_date — data da sessão web
    - user_id — identificador do usuário

- A tabela plans (dados sobre os planos):
 
    - plan_name — nome do plano
    - usd_monthly_fee — preço mensal em dólares americanos
    - minutes_included — pacote mensal de minutos
    - messages_included — pacote mensal de mensagens de texto
    - mb_per_month_included — volume do pacote de dados (em megabytes)
    - usd_per_minute — preço por minuto depois de exceder o limite do pacote (por exemplo, se o pacote inclui 100 minutos, o primeiro minuto excedente será cobrado)
    - usd_per_message — preço por mensagem de texto depois de exceder o limite do pacote
    - usd_per_gb — preço por gigabyte extra de dados após exceder o limite do pacote (1 GB = 1.024 megabytes)

## Etapas para conclusão do projeto

- Etapa 1: Inicialização
- Etapa 2: Carregar os dados
- Etapa 3: Pré-processamento dos dados e enriquecimento dos dados
- Etapa 4: Análise exploratoria de dados (EDA)
- Etapa 5: Calcular a receita
- Etapa 6: Teste hipóteses estatísticas
- Etapa 7: Conclusão

## 🛠 Habilidade
Python

<svg xmlns="http://www.w3.org/2000/svg" width="256" height="256" fill="none" viewBox="0 0 256 256"><rect width="256" height="256" fill="#242938" rx="60"/><path fill="url(#paint0_linear_2_47)" d="M127.279 29C76.5066 29 79.6772 51.018 79.6772 51.018L79.7338 73.8284H128.185V80.6772H60.4893C60.4893 80.6772 28 76.9926 28 128.222C28 179.452 56.3573 177.636 56.3573 177.636H73.2812V153.863C73.2812 153.863 72.369 125.506 101.186 125.506H149.24C149.24 125.506 176.239 125.942 176.239 99.4123V55.5461C176.239 55.5461 180.338 29 127.279 29ZM100.563 44.339C105.384 44.339 109.28 48.2351 109.28 53.0556C109.28 57.8761 105.384 61.7723 100.563 61.7723C95.7426 61.7723 91.8465 57.8761 91.8465 53.0556C91.8465 48.2351 95.7426 44.339 100.563 44.339Z"/><path fill="url(#paint1_linear_2_47)" d="M128.721 227.958C179.493 227.958 176.323 205.941 176.323 205.941L176.266 183.13H127.815V176.281H195.511C195.511 176.281 228 179.966 228 128.736C228 77.5062 199.643 79.323 199.643 79.323H182.719V103.096C182.719 103.096 183.631 131.453 154.814 131.453H106.76C106.76 131.453 79.7607 131.016 79.7607 157.546V201.412C79.7607 201.412 75.6615 227.958 128.721 227.958ZM155.437 212.619C150.616 212.619 146.72 208.723 146.72 203.903C146.72 199.082 150.616 195.186 155.437 195.186C160.257 195.186 164.154 199.082 164.154 203.903C164.154 208.723 160.257 212.619 155.437 212.619Z"/><defs><linearGradient id="paint0_linear_2_47" x1="47.22" x2="146.333" y1="46.896" y2="145.02" gradientUnits="userSpaceOnUse"><stop stop-color="#387EB8"/><stop offset="1" stop-color="#366994"/></linearGradient><linearGradient id="paint1_linear_2_47" x1="108.056" x2="214.492" y1="109.905" y2="210.522" gradientUnits="userSpaceOnUse"><stop stop-color="#FFE052"/><stop offset="1" stop-color="#FFC331"/></linearGradient></defs></svg>

## Bibliotecas utilizadas
- Pandas
- Numpy
- Seaborn
- Matplotlib
- scipy

## 🔗 Links
[![portfolio](https://img.shields.io/badge/my_portfolio-000?style=for-the-badge&logo=ko-fi&logoColor=white)](https://github.com/Oliverrafael
)
[![linkedin](https://img.shields.io/badge/linkedin-0A66C2?style=for-the-badge&logo=linkedin&logoColor=white)](https://www.linkedin.com/in/rafael-oliveira-528400335/
)
