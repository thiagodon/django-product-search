# django-product-search
Api de Busca de Produtos - Django - Elasticsearch
Instalação Poetry

```
$ curl -sSL https://raw.githubusercontent.com/python-poetry/poetry/master/get-poetry.py | python -
$ mkdir django-product-search && cd django-product-search
$ poetry init
$ poetry add django
$ etry run django-admin startproject product-search .
```

https://docs.docker.com/engine/install/ubuntu/

https://hub.docker.com/_/postgres

https://hub.docker.com/_/elasticsearch

docker-compose.yml
```
version: '3.8'
services:
  db:
    image: postgres:14.1-alpine
    shm_size: '2gb'
    restart: always    
    environment:
      - POSTGRES_USER=postgres
      - POSTGRES_PASSWORD=postgres
    ports:
      - '5432:5432'
    volumes: 
      - db:/var/lib/postgresql/data
  elasticsearch:
    image: docker.elastic.co/elasticsearch/elasticsearch:7.12.0
    ports:
      - 9200:9200
      - 9300:9300
    environment:
      discovery.type: "single-node"
      ES_JAVA_OPTS: "-Xms2g -Xmx2g"
      xpack.monitoring.enabled: "true"
    volumes:
      - elk:/var/lib/elasticsearch/data/
```

```  
$ docker-compose up -d
```  

```  
$ docker-compose exec postgres sh -c 'export PGPASSWORD=postgres && psql -h 127.0.0.1 -p 5432 -U postgres postgres -c "create database product-search"'
```

ou 

```
$ docker-compose exec postgres sh -c 'export PGPASSWORD=postgres && psql -h 127.0.0.1 -U postgres -d postgres'
CREATE DATABASE product-search;
exit;
```

```  
(env)$ cd product-search
(env)$ python ../manage.py startapp products
(env)$ cd ..
```  

product-search/settings.py
```  
INSTALLED_APPS = [
...
'product-search.products.apps.ProductsConfig',
...
]
```  
product-search/products/app.py

product-search/products/models.py

product-search/products/documents.py





