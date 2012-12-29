---
layout: getting_started
title: Começando - Configuração do Projeto

current: Configuração do Projeto
previous: Introdução
previous_url: /v1/docs/getting-started/introduction.html
next: Boxes
next_url: /v1/docs/getting-started/boxes.html
---
# Configuração do Projeto

O restante deste guia de iniciação foi escrito como um passo a passo. Como
leitor, você é encorajado a acompanhar os exemplos no seu próprio computador.
Como o Vagrant funciona com máquinas virtuais, não será deixada nenhuma
"sujeira" quando você terminar de usá-lo (nenhum software estranho, nem
arquivos etc.) pois o Vagrant se encarrega de destruir a máquina virtual
quando você quiser.

## Configuração do Projeto Vagrant

O primeiro passo em qualquer projeto que usa o Vagrant é definir o diretório
raiz e configurar os arquivos básicos necessários. O Vagrant fornece um
conveniente utilitário de linha de comando apenas para isso. Na transcrição do
terminal abaixo, criamos o diretório para nosso projeto e fizemos sua
inicialização com o Vagrant:

{% highlight bash %}
$ mkdir vagrant_guide
$ cd vagrant_guide
$ vagrant init
{% endhighlight %}

O `vagrant init` cria um Vagrantfile inicial. Por enquanto, vamos deixar o
Vagrantfile do jeito que está, mas ele será usado bastante nos passos futuros
para configurar nossa máquina virtual.

## Configuração do Projeto Web

Agora, com o Vagrant pronto nesse diretório, vamos criar um “projeto web”
rápido que iremos usar mais à frente para demonstrar nossa VM. Execute o
seguinte comando no diretório do seu projeto (o diretório que tem o
Vagrantfile):

{% highlight bash %}
$ echo "<h1>Hello from a Vagrant VM</h1>" > index.html
{% endhighlight %}

Os passos acima podem ser executados em qualquer ordem. O Vagrant pode ser
facilmente inicializado em pastas de projetos pré-existentes.

<div class="alert alert-block alert-notice">
  <h3>E quanto ao PHP? Python? Java?</h3>
  <p>
    Para manter esse guia de iniciação o mais simples e genérico possível,
    usamos como exemplo um projeto baseado em HTML, mas o Vagrant não faz
    nenhuma suposição sobre o tipo de projeto que você está desenvolvendo.
    Deve ficar claro depois de passar por todo o guia de iniciação que o
    Vagrant pode ser usado com qualquer tipo de projeto web.
  </p>
</div>
