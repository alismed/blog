---
lang: pt-br
layout: post
title: Automação de Testes
author: Alison Souza
twitter-img: /assets/img/automacao-testes.png
---

Sobre como automatizar testes usando Ruby on Rails.

Talvez você ainda não esteja aplicando [TDD](https://tdd.caelum.com.br/) (Test Driven Development), não considero um requisito, mas será mais fácil pensar na automação quando o ciclo proposto pelo TDD for aplicado.

Testes unitários São testes que verificam os critérios de aceite para um trecho de código específico. São criados para se certificar que partes do seu sistema estão funcionando corretamente. Ao escrever testes unitários, estes serão uma das partes mais importantes do desenvolvimento de uma aplicação.

## Motivação
**Não apenas porque:**
- Queremos evitar um tarefa repetitiva e eventualmente chata
- Aumentar a velocidade na execução do roteiro de testes
- Diminuir a chance do "herro umano"
- Aumentar a qualidade do código

**E também porque:**
- Possibilitará aplicarmos Integração Continua
- Diminui riscos com eventual rotatividade de equipe
- Diminui o medo do código legado
- Cria uma documentação executável dos testes
- Cria uma documentação viva
- Pode ser aplicado milhares de vezes (ou mais, rsrs)
- Feedback imediato sobre efeitos colaterais em outras partes do código
- Aumentar as chances de erros serem detectados nas fases de concepção
- Reduz custo do desenvolvimento e manutenção

Os benefícios podem depender do tamanho da sua cobertura de código. Acredito que quanto maior a cobertura de código, mas eficientes os testes podem ser. Contudo, esta não é uma opnião unanime. Interessante ter qualidade nos testes e buscar não a apenas a cobertura de linhas de código, mas também a cobertura dos cenários de testes.

Ponderando que seus testes podem seguir o conceito de pirâmide de [Mike Cohn](https://martinfowler.com/articles/practical-test-pyramid.html), as ferramentas abaixo irão apoiar.

## RSpec
Mais do que uma forma de criar testes de unidade, RSpec fornece uma forma de criar especificações executáveis do código.

Com o RSpec também é possível aplicar o [BDD](http://auditeste.com.br/o-que-e-bdd-e-quais-sao-os-seus-beneficios/) (Behaviour-Driven Development). Isso porque ao escrever o teste estaremos pensando no comportamento esperado para nosso código.

Para usar são necessários dois passos. Instalar a gem e configurar sua aplicação.

```shell
gem install rspec
```
  
Adicione no GemFile
```ruby
group :development, :test do
  gem 'rspec-rails', '~> 3.0'
end
```
  
Gerar specs
```shell
rails generate rspec:install
```

Outra vantagem do Rspec é a geração de relatórios. Imagine a cada commit gerar uma visão do que esta funcionando ou parou de funcionar?

```shell
rspec -f h -o rspec_report.html 
```
 
Os testes unitários podem/devem cobrir o MVC ao também conseguir aplicar testes nas views (html).

**Importante**, o simples fato de usar a técnica do BDD não trará a automação.

## Cucumber
O Cucumber não é apenas uma ferramenta de testes, mas também uma ferramenta para documentação de requisitos que permite a execução e automação de testes. Requisitos que foram escritos em formato de histórias do usuário. Ao executar testes sobre um requisito podemos estar validando mais de uma funcionalidade de uma vez.

## Selenium
Gosto do Selenium IDE. Com razoável facilidade é possível realizar testes de integração.

Além de auxiliar nos testes também me ajuda durante o desenvolvimento ao preencher os formulários extensos ou com muitas etapas.

Com maior facilidade é possível exportar para o RSpec e conseguir a automação.

## Cobertura de código
E como saber se a minha cobertura de código é suficiente? Uma solução é usarmos uma ferramenta de avaliação de código estático. O [simplecov](https://rubygems.org/gems/simplecov) pode ser associado ao Rspec gerando relatórios intuitivos e relevantes.

O assunto é extenso e vou parar aqui. Pretendo em artigos futuros abordar como escrever testes em cada ferramenta. Começar ao menos com o Rspec é uma boa alternativa e não exigirá muito.

**Para ir além**
- [Vertentes do Teste de Software](https://www.devmedia.com.br/desvendando-o-processo-de-teste-de-software/33287)
- [Better Specs](http://betterspecs.org/)
- [Test first](https://blog.cleancoder.com/uncle-bob/2013/09/23/Test-first.html)

