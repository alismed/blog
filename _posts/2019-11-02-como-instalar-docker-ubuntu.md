---
layout: post
lang: pt-br
author: Alison Souza
title: Como instalar o docker no Ubuntu
twitter-img: /assests/img/docker-whale.png
---

O roteiro abaixo monstra como executar a instalação no Ubuntu. Estes passos foram feitos para a versão `19.04`.

1. Garanta que a lista de pacotes esta atualizada com `sudo apt update`.
1. Um pré-requisito é a instalação de certificados.
1. Outro requisito é a instação de GPG Key.
1. Adicione o repositório do Docker.
1. Instale o Docker.
1. Configure o acesso de seu usuário.
1. Também instale e configure o `docker-compose`.


**Comandos**

```shell
sudo apt-get install apt-transport-https ca-certificates software-properties-common

curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo apt-key add -

sudo add-apt-repository "deb [arch=amd64] https://download.docker.com/linux/ubuntu $(lsb_release -cs) stable"

sudo apt-get update

sudo apt-get install -y docker-ce

sudo gpasswd -a ${USER} docker

sudo systemctl enable docker

sudo systemctl start docker
```


**Docker Compose**

```shell
sudo curl -L "https://github.com/docker/compose/releases/download/1.23.1/docker-compose-$(uname -s)-$(uname -m)" -o /usr/local/bin/docker-compose

sudo chmod +x /usr/local/bin/docker-compose 
```


**Validando**

Execute o `hellow world`.

```
docker run hello-world
```

Veja outros roteiros de instalação para o [Ubuntu](https://github.com/alismed/ubuntu-after-install).


