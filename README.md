# KPI_Automate
Automação de Relatórios de Performance IPI
Este projeto contém um conjunto de scripts para automatizar completamente a geração de relatórios de performance IPI, desde a extração de dados do Google Sheets até a criação de um relatório final em PDF.

Estrutura dos Arquivos
gerador_de_relatorios.py: O script principal que orquestra todo o processo. É o único arquivo que você precisa executar.

consultas_relatorio.py: Centraliza as consultas SQL usadas para popular o relatório PDF.

unification.sql: Seu script principal de cálculo e unificação dos dados.

config_mysql.json: (Ação Necessária) Arquivo com as credenciais do banco de dados.

credentials.json: (Ação Necessária) Arquivo de credenciais do Google Cloud para acessar as planilhas.

logo_empresa.png: (Ação Necessária) Imagem do logo da sua empresa para o cabeçalho do PDF.

requirements.txt: Lista de todas as bibliotecas Python necessárias.

Passo 1: Configuração do Ambiente
Você precisa ter o Python 3.6 ou superior instalado.

Crie um Ambiente Virtual (Recomendado)

Abra o terminal ou prompt de comando na pasta do projeto e execute:

python -m venv venv

Ative o ambiente:

Windows: venv\Scripts\activate

macOS/Linux: source venv/bin/activate

Instale as Bibliotecas Necessárias

Crie um arquivo chamado requirements.txt na pasta do projeto com o seguinte conteúdo:

# Bibliotecas para Análise de Dados e Conexão
pandas
numpy
SQLAlchemy
mysql-connector-python
openpyxl

# Bibliotecas para API do Google Sheets
gspread
oauth2client
google-auth
google-auth-oauthlib

# Bibliotecas para Geração e Manipulação de PDF
reportlab
fpdf2
PyMuPDF

# Bibliotecas para Gráficos e Imagens
matplotlib
Pillow

# Bibliotecas para Interface Gráfica e Web Scraping
customtkinter
beautifulsoup4

# Biblioteca para tratamento de texto (remover acentos)
unidecode

Instale todas de uma vez com o comando:

pip install -r requirements.txt

Passo 2: Obtenção das Credenciais
Google Sheets (API):

Siga um tutorial para criar uma Conta de Serviço no Google Cloud Platform. Pesquise por: "google sheets api service account python".

Durante o processo, você irá:

Ativar a API do Google Sheets e do Google Drive.

Criar uma Conta de Serviço.

Gerar e baixar um arquivo de chave JSON.

Renomeie este arquivo JSON para credentials.json e coloque-o na mesma pasta deste projeto.

Importante: Para cada planilha que o script precisa ler, você deve "Compartilhar" a planilha com o email da conta de serviço (o client_email que está dentro do arquivo credentials.json).

Passo 3: Configuração dos Arquivos
config_mysql.json: Crie este arquivo na mesma pasta do projeto. Abra-o e preencha as informações de conexão com o seu banco de dados MySQL (usuário, senha, host, porta e nome do banco). Use o endereço de IP correto no "host", como 172.32.2.62.

gerador_de_relatorios.py: Abra este arquivo e edite a seção CONFIGURAÇÕES:

SHEETS_PARA_CARREGAR: Este é um dicionário crucial. Para cada tabela que você quer carregar, adicione uma entrada no formato:
"nome_da_tabela_mysql": ["Nome Exato da Planilha no Google Drive", "Nome Exato da Aba"]

CAMINHO_LOGO_EMPRESA: Coloque o arquivo de imagem do seu logo (ex: logo_empresa.png) na mesma pasta do projeto e verifique se o nome corresponde.

CAMINHO_SCRIPT_SQL_PRINCIPAL: Verifique se o nome do seu script SQL está correto (ex: "unification.sql").

Passo 4: Execução
Depois de tudo configurado:

Certifique-se de que seu ambiente virtual está ativado.

Abra o terminal na pasta do projeto.

Execute o script principal:

python gerador_de_relatorios.py

O script irá solicitar que você digite o ano e o mês da análise.

Aguarde o processo ser concluído. Ele irá mostrar o progresso de cada etapa no terminal.

Ao final, um arquivo PDF (ex: Relatorio_IPI_08_2025.pdf) será criado na pasta do projeto.
