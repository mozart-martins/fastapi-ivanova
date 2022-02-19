


> Written with [StackEdit](https://stackedit.io/).


# Levantando os containers (Postgres e Pgadmin) e a rede

> docker-compose up

# Conectando-se ao Pgadmin

Usuário e senha estão passados no enviroment do service do docker file.

# Conectando-se ao Postgres

O usuário é o padrão (postgres) e a senha é a definida no enviroment do docker file.
Observação importante é que o endereço (host) do banco é o nome do service definido no docker file: postgres.

# Configurando o ambiente virtual no diretório do projeto

> python -m venv ./venv

# Instalando dependências

> pip install fastapi
> pip install uvicorn
> pip install sqlalchemy
> pip install databases
> pip install asyncpg
> pip install psycopg2
> pip install psycopg2-binary
> pip install alembic

Ou tudo em uma linha:

> pip install fastapi uvicorn sqlalchemy databases asyncpg psycopg2 psycopg2-binary alembic

# Rodando o arquivo main.py

> python -m uvicorn main:app --reload

# Comando para iniciar o Alembic

> alembic init migratrions

# Configurando o Alembic

No arquivo alembic.ini devemos colocar a correta string de conexão na variável sqlalchemy.url.

Já no arquivo env.py, deve-se importar o metadata (from main import metadata) do main.py ou de onde estiver configurado (metadata = sqlalchemy.MetaData()) e inserir na variável target_metadata, ficando target_metadata = metadata.

# Criando a primeira migration no Alembic

> alembic revision --autogenerate -m "Initial"

# Executando a migration

> alembic upgrade head

Para desfazer:

> alembic downgrade head
