# Projeto Delta

> Pipeline de Dados da Mútua

> Ambiente para desenvolvimento dos pipelines de dados, utilizando-se dos princípios de _Delta Lake_, camadas _Bronze_, _Silver_ e _Gold_ para disponibilização dos Dados.

## Ambiente
- **Spark**: ambiente para processamento dos dados com cluster de 3 servidores, sendo 1 master e 2 workers.
- **JupyterLab**: ambiente para desenvolvimento dos códigos com _pyspark_ e _spark-mssql-connector_.
- **Minio**: ambiente para armazenamento de objetos de alto desempenho, compatível com S3, sendo o _Data Lake_.

## Materiais de Referência
- https://medium.com/@ongxuanhong/dataops-02-spawn-up-apache-spark-infrastructure-by-using-docker-fec518698993 **Principal**
- https://github.com/arezamoosavi/AcidOnSpark-ETL
- https://github.com/cordon-thiago/airflow-spark/blob/master/docker/docker-compose.yml

## Requerimentos
- Pyhon
- Pip
- Docker

## Ambiente

### 1. Clonar o Projeto

```bash
git clone [URL]
```

### 2. Atualizar o gerenciador de pacotes

```bash
sudo apt-get update
```

### 3. Verificar e instalar o Python

Para verificar a instalação do Python

```bash
python3 --version
```

Caso o Python não esteja instalado

#### Ubuntu e Debian

```bash
sudo apt-get install python3.10
```

### 4. Verificar e instalr Pip

Para verificar a instalação do Pip

```bash
pip --version
```

Caso o Pip não esteja instalado

#### Ubuntu e Debian

```bash
sudo apt-get install python-pip
```

### 5. Criar o ambiente virtual (_venv_)

Criar o venv para utilizar o Python localmente no projeto

```bash
python3 -m venv .venv
```

Ativar o _venv_ para instalar todas as dependências somente para este projeto

```bash
source .venv/bin/activate
```

Instalar as dependências do projeto no _venv_

```bash
pip install -r requirements.txt
```

### 6. Instalar o Docker e docker-compose

Ver documentação

### 7. Criar containers

`make build` executará o comando `docker-compose build`

`make restart` executará o comando `docker-compose down` (removendo todos os containers que possam estar executando nesse projeto) e posteriormente executará o comando `docker-compose up -d` (subindo toso os containers de forma desanexada do terminal)

```bash
make build && make restart
```

`make nblog` executará o comando `docker logs spark-notebook` onde aparecerá a URL com o token de acesso ao _JupyterLab_

```bash
make nblog
```

> Consultar _makefile_ na raiz do Projeto

- A pasta _workspace_ na raiz do projeto aponta para a pasta _work_ do container _spark-notebook_ onde são armazenados o scripts
- A pasta _data_ na raiz do projeto aponta para a pasta _data_ do container _minio_ onde são armazenados os buckets com os obejtos armazenados

### Acessar

- Spark http://localhost:8080
- JupyterLab http://localhost:4040 (ver item 7 para verificar o link com _token_)
- Minio http://localhost:9001
