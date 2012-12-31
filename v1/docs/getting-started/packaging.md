---
layout: getting_started
title: Começando - Empacotamento

current: Empacotamento
previous: Redirecionamento de Portas
previous_url: /v1/docs/getting-started/ports.html
next: Desmontagem
next_url: /v1/docs/getting-started/teardown.html
---
# Empacotamento

Com a máquina virtual funcionando e pronta, estamos prontos para trabalhar.
Mas vamos supor que você tem outras pessoas em sua equipe, e que você quer
compartilhar o mesmo ambiente virtual com eles. Vamos empacotar esse novo
ambiente dentro de uma box para eles, assim eles podem começar a trabalhar
com apenas alguns comandos.

Os pacotes são imagens exportadas do seu ambiente virtual atual que podem ser
distribuídas facilmente. Eles geralmente são sufixados com uma extensão "box",
por isso eles são conhecidos como arquivos box. Opcionalmente, Vagrantfiles
podem ser incluídos nas boxes de modo a especificar portas redirecionadas,
pastas compartilhadas etc.

Antes de continuar seguindo pelo restante desta página, tenha certeza que o
ambiente virtual já foi criado pelo comando `vagrant up`.

## Criando um Vagrantfile

Primeiro, vamos criar um Vagrantfile básico que iremos empacotar com a box
para redirecionar a porta web. Dessa forma, os usuários da box podem
simplesmente adicionar a box, rodar um `vagrant up` e tudo estará funcionando,
incluindo o HTTP! Crie um novo arquivo, que será usado como o Vagrantfile da
box. Nomeie o arquivo como `Vagrantfile.pkg` e ponha nele o seguinte conteúdo:


{% highlight ruby %}
Vagrant::Config.run do |config|
  # Redirecione o apache
  config.vm.forward_port 80, 8080
end
{% endhighlight %}

<div class="info">
  <h3>O que é o endereço MAC?</h3>
  <p>
    Quando um sistema operacional é instalado, ele geralmente define o endereço
    MAC associado à interface de rede <code>eth0</code>, o que permite que
    a VM se conecte à internet. Mas quando importamos uma base, o VirtualBox
    altera o endereço para um novo, o que quebra a <code>eth0</code>. O
    endereço MAC da base precisa ser persistido no Vagrantfile da box para que
    o Vagrant possa configurar o endereço MAC para garantir a conectividade da
    internet.
  </p>
</div>

## Empacotando o Projeto

Execute o código a seguir para empacotar o ambiente:

{% highlight bash %}
$ vagrant package --vagrantfile Vagrantfile.pkg
{% endhighlight %}

O `vagrant package` pega o ambiente virtual do projeto atual e o empacota
num arquivo `package.box` no mesmo diretório. A opção `--vagrantfile` indica
ao `vagrant package` para incluir as linhas do redirecionamento de portas do
`Vagrantfile.pkg` dentro da box, assim as VMs criadas usando essa box terão
automaticamente o redirecionamento de portas configurado para elas, sem que
o usuário tenha que editar o `Vagrantfile` das suas VMs (as boxes tem seus
próprios `Vagrantfiles` -- para mais detalhes sobre como isso funciona, veja a
[documentação dos Vagrantfiles](http://vagrantup.com/v1/docs/vagrantfile.html)).

## Distribuindo a Box

O Vagrant atualmente suporta a instalação de boxes do sistema de arquivos
local ou via HTTP. Se a box que você estiver distribuindo tiver dados privados
nela (como uma aplicação web da empresa, ou um trabalho de um cliente de um
freelance), então você deveria a box em um sistema de arquivos seguro onde
o acesso não seja público.

Se a box que você estiver distribuindo destina-se a ser pública, o HTTP é o
melhor recurso para ela, assim qualquer um pode baixá-la facilmente.

Uma vez que a box estiver no lugar, outros desenvolvedores podem adicioná-la
e utilizá-la como qualquer outra box. O exemplo abaixo é seguindo a visão de
um novo desenvolvedor na sua equipe usando sua box recentemente empacotada:

{% highlight bash %}
$ vagrant box add my_box /path/to/the/package.box
$ vagrant init my_box
$ vagrant up
{% endhighlight %}

Nesse ponto, eles devem ter um ambiente totalmente funcional, que reflete
exatamente o ambiente configurado nos passos anteriores deste guia. Observe que
eles não precisaram fazer nenhum provisionamento, nem configurar nada em
seus sistemas etc. (além do Vagrant). Distribuir ambientes de desenvolvimento
nunca foi tão fácil.
