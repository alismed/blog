---
layout: post
lang: pt-br
author: Alison Souza
title: Acessando Redis com Ruby
twitter-img: /assets/img/redis.png
---
Redis é um banco de dados não relacional, NoSQL.

O Redis é muito rápido tanto para escrita como para leitura porque armazenar seus dados em memória. Dados que são armazenados na forma de chave-valor.

Neste post apenas um pouco do que podemos fazer. Quem sabe com o tempo consiga escrever mais?

Para instalar a gem.

```shell
gem install redis
```

### Conexão
```ruby
require 'redis'
  
redis = Redis.new(:host => "10.0.1.1", :port => 6380)
 

Hello World
puts redis.echo "hello"
  
# server should respond with PONG
puts redis.ping
```
 

### Armazenando strings
Trabalhando com strings, define-se uma chave e um valor. Para tanto são usados os comandos set e get.

```ruby
# set
redis.set("value:product", "300")
redis.set("value:product:20150312", "300, 3002")
  
# get
redis.get "value:product"
redis.get "value:product:20150312"
  
# para listar as chaves que existem eh possivel fazer pesquisas
redis.keys "*:*:2015*"
```
 

### Como servidor de cache
Definimos um tempo de expiração com setex.

```ruby
# com setex passamos o tempo em segundos
redis.setex 'key-name', 5, 'string-value'
  
# get antes de 5 segundos
redis.get "key-name"
=> "string-value"
  
# depois de 5 segundos 
redis.get "key-name"
=> nil
```
 

### Outras possibilidades

O Redis consegue armazenar além de strings outros tipos de dados que permitem um uso mais avançado:
- int
- float
- hash
- lists

Além de servidor de cache pode ser usado como:
- Gerenciador de sessão
- Tabela de classificação
- Servidor de Fila, Mensageria
- Solução de Publish e Subscribe
- Uma base de dados não relacional
 

**Para ir além**

- [Redis](https://try.redis.io/)
- [EXPIRE key seconds](https://redis.io/commands/expire) 
- [A Ruby client library for Redis](https://github.com/redis/redis-rb) 
- [Cache Redis do Azure](https://azure.microsoft.com/pt-br/services/cache/)
 
