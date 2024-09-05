---
layout: post
lang: pt-br
author: Alison Souza
title: Localstack
twitter-img: /assets/img/localstack.png
---

Como instalar e utilizar o Localstack para testes de AWS em ambiente local

Requisitos
- Docker
- AWS cli
- jq

## Setup
Para realizar a instalação baixe a imagem [oficial do localstack](https://hub.docker.com/r/localstack/localstack)
```shell
docker pull localstack/localstack
```

Para iniciar exeute a imagem no modo interativo. O parâmetro `-d` é opcional para liberar o prompt.
```shell
docker run --rm -d -p 4566:4566 -p 4571:4571 localstack/localstack
```

Para validar execute o comando abaixo:
```shell
curl http://localhost:4566/_localstack/info | jq
```

## Parametrização

Crie um profile com valores ficticios de uma conta aws
```shell
aws configure --profile lstk
```

Acrescente o parâmetro `endpoint_url`ao final do arquivo
```shell
echo 'endpoint_url = http://localhost:4566' >> ~/.aws/config
```

## utilização

Para a utilização deve se usar o parâmetro `--profile` com a configuração recem criada. Uma opção é usar a variável de ambiente `AWS_DEFAULT_PROFIL' usando o comando `export`.

No exemplo abaixo, vamos criar um bucket e listá-lo.
```shell
aws s3 ls --profile lstk
aws s3 mb s3://alismed-labs --profile lstk
aws s3 ls --profile lstk
```

<br>