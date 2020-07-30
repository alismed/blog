---
layout: post
lang: pt-br
author: Alison Souza
title: SSH seguro em linux desktops
twitter-img: /assets/img/ssh.png
---

Configurando o [SSH](https://en.wikipedia.org/wiki/Secure_Shell) de forma segura em GNU/Linux desktop.

Primeira pergunte-se: Preciso deste serviço ativo? Caso não tenha uma boa resposta, o ideal seria deixar o mesmo inativo:

```shell
sudo systemctl stop sshd
sudo systemctl disable sshd
```

Certo, você tem uma necessidade real. Então vamos deixar mais seguro. Realize as alterações abaixo no arquivo: `/etc/ssh/sshd_config`. Adicione linhas e/ou remova comentários.

### Timeout Interval

Sessões inativas serão derrubadas. Configure o intervalo em segundos.
```shell
ClientAliveInterval 300
ClientAliveCountMax 0
```

### Empty Passwords

Não permita que o acesso ocorra através de contas com senhas vazias.
```shell
PermitEmptyPasswords no
```

### Access

Limite o acesso para uma lista de usuários autorizados.
```shell
AllowUsers user_a user_b user_c
```

### Root Logins

Desabilite o login por uma conta root. Use uma conta com menos privilégios, caso precise elevar os acesso, mude para o usuário root. 
```shell
PermitRootLogin no
```

### SSH Protocol 2

Use apenas a versão mais recente.
```shell
Protocol 2
```

### Port

Use uma porta diferente da porta padrão. Cuidado na escolha da nova [porta](https://en.wikipedia.org/wiki/List_of_TCP_and_UDP_port_numbers).
```shell
Port 2222
```
A porta do exemplo acima é tão conhecida como a porta padrão. Use outro valor!

Após as configurações reinicie o serviço.

Outra opção é usar chave criptográfica ao invés de senhas. Vou deixar esta explicação para outra oportunidade.

