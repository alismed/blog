---
layout: post
lang: pt-br
author: Alison Souza
title: Docker como Ambiente de Desenvolvimento Ruby on Rails
twitter-img: /assets/img/docker-ruby.png
---
 
Um boa opção para montar seu ambiente de desenvolvimento [Ruby on Rails](https://rubyonrails.org/) é usando o [Docker](https://www.docker.com/) e o [Docker Compose](https://docs.docker.com/compose/).

Permite isolar seu ambiente ruby, banco de dados, sidekiq e outros componentes que compõem sua solução.

## As vantagens são:
- Inicialização em segundos
- Padronização do ambiente
- Tratar a infraestrutura do ambiente como código que pode ser versionado

## Setup

Neste [repositório](https://github.com/alismed/DockerFiles/tree/master/RailsApp) há um exemplo. Altere o arquivo DockerFile para mudar a versão do Ruby e nome do projeto/aplicação. Mude o arquivo docker-compose.yml para editar as informações do banco de dados e nome do projeto.

Considerando que o docker já esta instalado:

1. Para baixar a imagem do MySQL execute docker `pull mysql`.
1. Crie um diretório com o nome da aplicação/projeto.
1. Copie os quatro arquivos para esta pasta.
1. Execute o comando `docker-compose build` para criar a nova imagem.
1. O passo anterior pode levar alguns minutos, em seguida execute `docker-compose run web rails-api new .`
    - Isto irá criar uma nova aplicação Rails com o mesmo nome da pasta.
1. Digite yes quando for perguntado sobre sobrescrever o arquivo `Gemfile`.
1. Edite o arquivo `config/database.yml` com as informações de acesso ao banco de dados.
1. Para criar o database execute docker-compose run web `rails db:create`.
1. Para iniciar o ambiente: `docker-compose up web`.
1. O aplicativo esta pronto para ser acessado `http://localhost:3000`.

### Para executar outros comandos:
1. Para criar modelos, views e etc, use o comando `docker-compose run web rails g <something> <options>`.
1. Execute `docker-compose run web rails db:migrate`.

O Docker é uma ótima alternativa para virtualizar ambiente de desenvolimento, endereçando a criação de máquinas através da criação e execução de scripts. Padroniza a permite que todos na equipe estejam usando a mesma versão do ambiente.


