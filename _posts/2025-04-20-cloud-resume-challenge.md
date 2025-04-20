---
layout: post
lang: pt-br
author: Alison Souza
title: Cloud resume challenge
twitter-img: /assets/img/cloud-resume-challenge.png
---

Minha esperiência com o [The Cloud Resume Challenge - AWS](https://cloudresumechallenge.dev/docs/the-challenge/aws/).

Minha intenção ao "aceitar o desafio" era praticar e tirar a ferrugem escrevendo código. Não segui os dezesseis passos na ordem sugerida. Comecei o desafio pelo terraform pois queria um cenário onde a criação do projeto de ponta a ponta ocorreria a partir da infraestrutura como código.

Usei apenas um [repositório](https://github.com/alismed/cloud-resume-challenge) para todos os itens: database, backend e frontend. Depois desta experiência diria que separar os repositórios me parece o caminho mais adequado.

Interessante comentar que estou descrevendo apenas o resultado final, sem os erros e as validações e aprendizados que 

Meu processo foi realizado em partes. Foi realizado durante alguns dias, sempre que sobrava um tempinho. Em cada dia eu tentava executar alguma pequena parte, deixando algo funcionando. Talvez meus commits tenham ficado grandes, mas eu não queria deixar algo sem estar funcionando.

Escolhi a AWS e espero poder em futuro próximo praticar com a Azure. Tentei usar ao máximo a versão não licenciada do [localstack](https://www.localstack.cloud/), contudo em dado momento eu executava direto em minha conta pessoal da AWS. Apenas tomava muito cuidado para buscar as opções mais baratas ou até mesmo dentro do free tier. Além disso, sempre executava o metódo destroy do terraform antes de realizar o commit.

Comecei com site estático, criando o bucket S3 e levando um site com dois arquivos html e um arquivo css. Neste momento de fato apenas criei o bucket, sem o cloud front. Ou seja, deixei a opção `Static website hostingconfi` habilitado e permitindo acesso público. Lembrando que eu destruia o ambiente ao final de cada etapa.

Em um segundo momento adicionei o cloud front. E para tanto precisei alterar alterar as permissões do S3. Este deixou de ser público e apenas o cloud front teria permissão de acessa-lo.

O próximo item foi o database, o DynamoDB. Junto com a criação da tabela eu já criava um registro via terraform, chamei de "seed". Na verdade o único registro que esta solução vai ter.

Entre cada dia eu tentava voltar no que já havia realizado e fazer alguma revisão. Removendo algum hard code, criando uma variável, removendo algo. Usava o copilot como "buddy", tentando fazer perguntas sobre boas práticas, padrões, compreensibilidade ou até mesmo explicando o que estava fazendo, algo próximo do rubber duck debugging. 

Na sequência eu criei a Lambda. Usei o Python na versão 3.12. Aqui eu usei bastante o GitHub Copilot. Meu maior foco estava em escrever o terraform. E neste momento eu comecei a quebrar em módulos. Até então estava todo o código na pasta `infra`. Contudo eu apenas executava a criação do database usando o parâmetro `-chdir` para apenas executar os arquivos do módulo de backend, como se fosse um projeto único com a Lambda. Claro, aproveiatava para executar a criação do database e validar a execução da lambda aleterando o registro único da tabela.

Na sequência, sempre em um diferente dia, criei o API Gateway. E precisava voltar para alterar as permissões de acesso da Lambda, alterando a policy e restringindo acesso apenas pelo api gateway, pois no primeiro momento não tomei este cuidado. Após a execução do terraforma, usando as saídas que eu deixava no `outputs.tf` eu já reaizava a chamada via curl do endpoint validando o sucesso ou não.

Neste ponto eu voltei ao site estático, criando o javscript que chamaria o api gateway. Como a criação do cloud front demorava alguns minutos, criei um `mock` para facilitar, acabei não versionando mas basicamente era um endpoint com um json de saída simulando meu backend.

Como eu criava os itens em separado, ao ter todos os módulos prontos eu precisei fazer refatorações ajustando paths e estruturas. Usei bastante a opção `init -upgrade`, `validate` e `plan`. Busquei um código enxuto, mas acredito que ainda pode ficar melhor.

O próximo passo será criar as actions do GitHub. Volto depois para atualizar