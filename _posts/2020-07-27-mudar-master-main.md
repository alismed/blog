---
layout: post
lang: pt-br
author: Alison Souza
title: Mudar branch Master para Main
twitter-img: /assets/img/git-branch.png
---

Como mudar a branch master para main no GitHub.

Estou considerando meus projetos pessoais que não possuem automações como esteiras de CI/CD ou Hooks.

> Para esta ação não havia pendências em minhas branchs locais.

1. Faça a alteração local primeiro:
```shell
git branch -m master main
```

2. O comando abaixo vai criar uma nova branch `main` no repositório remoto.
```shell
git push -u origin main
```

> Estou usando o GitHub, para outras soluções de versionamento consulte a respectiva documentação para esta etapa a seguir.

3. Agora é preciso alterar as configurações remotas do repositório. Para alterar a branch padrão vá em: _Settings_, _Branches_ e altera a 'Default branch' main.

4. De volta ao código, aba _Code_, você conseguirá apagar a branch master.


**Veja Também**
- [git branch](https://git-scm.com/docs/git-branch#Documentation/git-branch.txt---move)
- [GitHub abandons 'master' term to avoid slavery row](https://www.bbc.com/news/technology-53050955)

