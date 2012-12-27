---
layout: getting_started
title: Começando - Por que o Vagrant?

current: Por que o Vagrant?
previous: Visão Geral
previous_url: /v1/docs/getting-started/index.html
next: Introdução
next_url: /v1/docs/getting-started/introduction.html
---
# Por que o Vagrant?

Desenvolvedores web usam ambientes virtuais todo dia com suas aplicações web.
Desde o EC2 e Rackspace Cloud até soluções especializadas como o EngineYard e o
Heroku, a virtualização é a ferramenta preferida para facilitar a implantação 
e o gerenciamento de infraestrutura. O Vagrant visa usar esses mesmos
princípios e colocá-los para trabalhar no coração do ciclo de vida da
aplicação. Por meio do fornecimento de máquinas virtuais fáceis de configurar,
leves, reproduzíveis e portáteis, direcionadas para ambientes de
desenvolvimento, o Vagrant ajuda a maximizar tanto sua produtividade e sua
flexibilidade quanto as de sua equipe.

O Vagrant é uma ferramenta de desenvolvimento que se baseia sobre os ombros de
gigantes, usando tecnologias testadas e aprovadas para fazer sua mágica. O
Vagrant usa o [VirtualBox da Oracle](http://www.virtualbox.org) para criar
suas máquinas virtuais e então usa o [Chef](http://www.opscode.com/chef) ou o
[Puppet](http://www.puppetlabs.com/puppet) para provisioná-las.

## Benefícios de Usar o Vagrant

### Para Desenvolvedores Individuais

Manter ambientes de desenvolvimento consistentes ao longo de múltiplos
projetos é simplesmente uma tarefa inviável para um desenvolvedor web moderno.
Cada projeto depende de suas próprias bibliotecas, sistemas de fila de
mensagens, bancos de dados, frameworks e mais, cada um com suas próprias
versões. Além das dependências, rodar tudo isso em uma única máquina pessoal e
lembrar-se de desligar tudo no fim do dia ou quando estiver trabalhando em
outros projetos também é inviável. O Vagrant fornece a você as ferramentas
para construir ambientes de desenvolvimento únicos para cada projeto de uma
vez, e depois facilmente derrubá-los e reconstruí-los apenas quando eles forem
necessários para que você economize tempo e frustação.

### Para Equipes

Todos os membros de uma equipe idealmente têm ambientes de desenvolvimento
idênticos: mesmas dependências, mesmas versões, mesmas configurações, mesmo
tudo. Mas isso simplesmente não é a verdade atualmente. Com os ORMs agnósticos
de banco de dados, múltiplas opções de servidors web e bibliotecas que evoluem
rapidamente, um membro da equipe pode estar usando o MySQL com uma versão de
uma biblioteca enquanto outro membro do time pode estar usando PostgreSQL com
outra versão da mesma biblioteca. Ou talvez a configuração do servidor de um
membro da equipe seja ligeiramente diferente. Todos esses são casos reais que
estão destinados a causarem problemas reais em algum momento futuro. O Vagrant
dá para as equipes a possibilidade de garantir um ambiente virtual de
desenvolvimento consistente e portátil que seja fácil e rápido de criar.

### Para Empresas

Se você já fez manutenção em uma aplicação web grande, uma das partes mais
difíceis é acrescentar novos recursos. Filas de mensagens, cache, servidores
de banco de dados e outros pontos de infraestrutura significam uma série de
instalações e um monte de outras configurações (veja [case-in-point: insanity](http://www.robbyonrails.com/articles/2010/02/08/installing-ruby-on-rails-passenger-postgresql-mysql-oh-my-zsh-on-snow-leopard-fourth-edition)).
O Vagrant fornece a você as ferramentas para construir um ambiente de
desenvolvimento uma vez e depois distribuí-lo facilmente para os novos membros
da sua equipe de desenvolvimento, dessa forma você pode colocá-los para
trabalhar e economizar tempo, dinheiro e frustação.
