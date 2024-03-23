# DBT 

### About DBT
Baseando em models, que são similares as tasks do airflow.
Usamos o models para criação do pipelines de transformação dos dados.
Cada desenvolvedor tera seu schema, o dbt separa por schemas os dados criados de diversas fontes.
Similar aos branchs do GitHub, ele vai rodar na produção o que estiver na main.
Os Jobs são as execuções dos enviroments, que são os deploys da branch main.

### Commands for DBT
Para executar o dbt
- dbt run

Para executar um modelo especifico do dbt
- dbt run --models {models_name}

Para gerar documentação do dbt models
- dbt docs_generate

Rodar apenas os testes
- dbt test