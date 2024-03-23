### PostgreSQL
- Operation database.
- Read only access.
- Commonly used to maintain data integrity and recording.
  
### Snowflake
- Commonly used to create DataWarehouses.
- Disponibility of data in real time.

- Script Snowflake
```
create database novadrive;
create schema stage;
 
CREATE WAREHOUSE DEFAULT_WH;
 
CREATE TABLE veiculos (
    id_veiculos INTEGER,
    nome VARCHAR(255) NOT NULL,
    tipo VARCHAR(100) NOT NULL,
    valor DECIMAL(10, 2) NOT NULL,
    data_atualizacao TIMESTAMP_LTZ,
    data_inclusao TIMESTAMP_LTZ
);
 
CREATE TABLE estados (
    id_estados INTEGER,
    estado VARCHAR(100) NOT NULL,
    sigla CHAR(2) NOT NULL,
    data_inclusao TIMESTAMP_LTZ,
    data_atualizacao TIMESTAMP_LTZ
);
 
CREATE TABLE cidades (
    id_cidades INTEGER,
    cidade VARCHAR(255) NOT NULL,
    id_estados INTEGER NOT NULL,
    data_inclusao TIMESTAMP_LTZ,
    data_atualizacao TIMESTAMP_LTZ
 
);
 
CREATE TABLE concessionarias (
    id_concessionarias INTEGER,
    concessionaria VARCHAR(255) NOT NULL,
    id_cidades INTEGER NOT NULL,
    data_inclusao TIMESTAMP_LTZ,
    data_atualizacao TIMESTAMP_LTZ
);
 
CREATE TABLE vendedores (
    id_vendedores INTEGER,
    nome VARCHAR(255) NOT NULL,
    id_concessionarias INTEGER NOT NULL,
    data_inclusao TIMESTAMP_LTZ,
    data_atualizacao TIMESTAMP_LTZ
);
 
CREATE TABLE clientes (
    id_clientes INTEGER,
    cliente VARCHAR(255) NOT NULL,
    endereco TEXT NOT NULL,
    id_concessionarias INTEGER NOT NULL,
    data_inclusao TIMESTAMP_LTZ,
    data_atualizacao TIMESTAMP_LTZ
);
 
CREATE TABLE vendas (
    id_vendas INTEGER,
    id_veiculos INTEGER NOT NULL,
    id_concessionarias INTEGER NOT NULL,
    id_vendedores INTEGER NOT NULL,
    id_clientes INTEGER NOT NULL,
    valor_pago DECIMAL(10, 2) NOT NULL,
    data_venda TIMESTAMP_LTZ,
    data_inclusao TIMESTAMP_LTZ,
    data_atualizacao TIMESTAMP_LTZ
);
```

### Apache Airflow
- Dag are Airflow steps and process (tasks).
- É um orquestrador de dados, realiza o processamento dos dados.
- É em Batch.
- 

### DBT
- Using Jinja2 and SQL

### For Example
host: 159.223.187.110
dbname ou database ou banco de dados: novadrive
user ou usuário: etlreadonly
password ou senha: novadrive376A@
port ou porta: 5432

Para acesso ao Sistema de Vendas:
http://143.244.215.137:3002/
Login: vendedor1
Senha: ia_nova_drive
Para consultar uma venda pelo ID da venda:
http://143.244.215.137:3002/procura

### Comands Instalation Docker engine
- sudo apt-get update
- sudo apt-get install ca-certificates curl gnupg lsb-release
- sudo mkdir -m 0755 -p /etc/apt/keyrings
- sudo curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo gpg --dearmor -o /usr/share/keyrings/docker-archive-keyring.gpg
- echo "deb [arch=$(dpkg --print-architecture) signed-by=/usr/share/keyrings/docker-archive-keyring.gpg] https://download.docker.com/linux/ubuntu   $(lsb_release -cs) stable" | sudo tee /etc/apt/sources.list.d/docker.list > /dev/null
- sudo apt-get update
- sudo apt-get install docker-ce docker-ce-cli containerd.io docker-buildx-plugin docker-compose-plugin
- curl -LfO 'https://airflow.apache.org/docs/apache-airflow/stable/docker-compose.yaml'

### Install Airflow
Criamos diretórios para arquivos do Airflow
- mkdir -p ./dags ./logs ./plugins

Usado para permissões
- echo -e "AIRFLOW_UID=$(id -u)" > .env

Inicializar o Docker
- sudo docker compose up -d
* o uso do -d é para modo desaclopado
- sudo docker ps
- sudo docker compose stop