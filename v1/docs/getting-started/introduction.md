---
layout: getting_started
title: Começando - Introdução

current: Introdução
previous: Por que o Vagrant?
previous_url: /v1/docs/getting-started/why.html
next: Configuração do Projeto
next_url: /v1/docs/getting-started/setup.html
---
# Introdução

Essa parte inicial fará a introdução aos binários e ao Vagrantfile, que são
usados de forma extensiva no controle do Vagrant. O restante dos guias de
iniciação presume que se tenha esse conhecimento básico.

## O Binário do Vagrant

Depois de instalado, o Vagrant geralmente é controlado com o comando `vagrant`
na interface de linha de comando. O binário `vagrant` tem muitos “subcomandos”
que podem ser invocados para manipular todas as funcionalidades do Vagrant,
como o `vagrant up`, o `vagrant ssh` e o `vagrant package`, só para listar
alguns. Para descobrir todos os subcomandos suportados, execute `vagrant`
apenas e todos serão listados para você.

## O Vagrantfile

Um `Vagrantfile` está para o Vagrant assim como um o `Makefile` está para o
Make. O `Vagrantfile` fica na raiz de todo projeto Vagrant e é usado para
configurar e definir o comportamento do Vagrant e da máquina virtual que ele
cria. Segue um Vagrantfile básico para você ter um breve ideia de como ele se
parece:

{% highlight ruby %}
Vagrant::Config.run do |config|
  # Setup the box
  config.vm.box = "my_box"
end
{% endhighlight %}

Como você pode ver, um Vagrantfile é apenas um código Ruby, que em geral
contém um bloco de configuração do Vagrant. Na maioria dos comandos, o Vagrant
primeiramente carregará o Vagrantfile do projeto para configuração.
