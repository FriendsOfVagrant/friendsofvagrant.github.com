---
layout: getting_started
title: Começando

current: Visão Geral
next: Por que o Vagrant?
next_url: /v1/docs/getting-started/why.html
---
# Começando com o Vagrant

O Vagrant usa o [VirtualBox da Oracle](http://www.virtualbox.org)
para criar dinamicamente máquinas virtuais configuráveis, leves e portáteis.
O primeiro conjunto de páginas serve para introduzir você ao Vagrant e ao que
ele tem a oferecer, enquanto o restante do guia é um passo a passo técnico para
a construção de um ambiente de desenvolvimento web totalmente funcional. O
guia de iniciação termina explicando como empacotar o novo ambiente que o
vagrant criou para que outros desenvolvedores possam iniciá-lo e o colocá-lo
para rodar com apenas alguns comandos.

## Obtenha o VirtualBox

O Vagrant depende do [VirtualBox da Oracle](http://www.virtualbox.org) para
criar todo o seu ambiente virtual. O VirtualBox é um virtualizador completo de
uso geral para hardware x86. Voltado para utilização em servidores,
desktops e dispositivos embarcados, ele é uma solução de virtualização com
qualidade profissional, além de ser um software de código aberto. O VirtualBox
roda no **Windows**, no **Mac OS X**, no **Linux** e no **Solaris**.

Aqui está um link direto para a [página de download](http://www.virtualbox.org/wiki/Downloads).

O Vagrant atualmente suporta o VirtualBox 4.0.x, o 4.1.x e o 4.2.x.

## Instale o Vagrant

Para instalar o Vagrant, baixe o pacote ou o instalador apropriado a partir da
[página de download](http://downloads.vagrantup.com) e faça a instalação
usando os procedimentos padrões do sistema operacional. No Windows e no
Mac OS X, o comando `vagrant` deve ser colocado automaticamente no seu `PATH`.
Nos outros sistemas, você terá que adicionar `/opt/vagrant/bin` ao seu `PATH`.

Se um pacote Vagrant não estiver disponível para sua plataforma, você também
pode fazer a instalação usando o a [RubyGems](http://rubygems.org/gems/vagrant)
via `gem install vagrant`. No entanto perceba que os pacotes são os métodos de instalação preferidos e melhor suportados.

## Seu Primeiro Ambiente Virtual com o Vagrant

<pre>
$ vagrant box add lucid32 http://files.vagrantup.com/lucid32.box
$ vagrant init lucid32
$ vagrant up
</pre>

Enquanto o resto do guia de iniciação irá focar em explicar como construir uma
máquina virtual completamente funcional para servir aplicações Rails, você
precisa se acostumar com o trecho de código acima. Depois da configuração
inicial de todo ambiente Vagrant, esse trecho será tudo que um desenvolvedor
precisará para criar seu ambiente de desenvolvimento! Perceba que o trecho
acima por fim cria uma máquina virtual totalmente funcional de 512MB que roda
Ubuntu no background, embora a máquina não faça muita coisa nesse ponto.
