---
layout: getting_started
title: Começando - Provisionamento

current: Provisionamento
previous: SSH
previous_url: /v1/docs/getting-started/ssh.html
next: Redirecionamento de Portas
next_url: /v1/docs/getting-started/ports.html
---
# Provisionamento

As boxes nem sempre são configuradas em único passo no seu ambiente Vagrant.
Na maioria das vezes as boxes serão utilizadas como uma base para uma
configuração mais complicada. Por exemplo: talvez você esteja criando uma
aplicação web que usa o AMQP e alguns worker daemons personalizados no
background. Nessa situação, seria mais fácil usar a box base e então adicionar
o software personalizado em cima dela (e depois empacotar tudo para que outros
possam utilizar o pacote mais facilmente, vamos abordar isso mais à frente).

Felizmente, o Vagrant já vem com provisionamento embutido no código, seja
usando o [chef](http://www.opscode.com/chef), tanto o
[chef solo](http://wiki.opscode.com/display/chef/Chef+Solo)
quanto o [chef server](http://wiki.opscode.com/display/chef/Chef+Server), ou
usando o [Puppet](http://www.puppetlabs.com/puppet), ou ainda você pode
[estender o vagrant](/v1/docs/provisioners/others.html) para suportar mais
provisionadores, um tópico avançado que não será abordado aqui.

Para nosso site HTML básico, vamos mostrar como você pode usar o
provisionamento, Chef e Puppet, para configurar o Apache para servir um site.
Observe que você deveria escolher qual deles testar (ou o Chef ou o Puppet),
ou testar ambos, no entanto garanta que você executou um `destroy` e um `up` na
sua VM entre os testes, assim você iniciará em um ambiente limpo.

## Configurando o Chef e o Vagrant

Como um tutorial de como usar o Chef está fora do escopo deste guia de
iniciação, empacotamos previamente os cookbooks para seu provisionamento. Você
tem apenas que configurar seu Vagrant para apontar para ele:

{% highlight ruby %}
Vagrant::Config.run do |config|
  config.vm.box = "lucid32"

  # Habilita e configura o provisionador chef solo
  config.vm.provision :chef_solo do |chef|
    # Vamos baixar nossos cookbooks da web
    chef.recipe_url = "http://files.vagrantup.com/getting_started/cookbooks.tar.gz"

    # Diga ao chef qual recipe será executada. Nesse caso, a receita `vagrant_main`
    # faz toda a mágica.
    chef.add_recipe("vagrant_main")
  end
end
{% endhighlight %}

Observe que apesar de usarmos uma URL para baixar os cookbooks desse nosso
projeto, você também pode colocar os cookbooks em um diretório local, o que é
interessante para armazenar seus cookbooks num controle de versão junto do seu
projeto. Mais detalhes sobre o assunto podem ser encontrados na
[documentação do chef solo](/v1/docs/provisioners/chef_solo.html).


## Configurando o Puppet e o Vagrant

Alternativamente, você pode usar o Puppet para configurar o Apache. Para isso
criamos um diretório chamado `manifests` (na raiz onde o Vagrantfile está
localizado) e criamos um arquivo para manter nossa configuração do Puppet,
por exemplo `default.pp`.

Veja que tanto o caminho quanto o nome do arquivo pode ser configurado, mas o
Vagrant deixa como padrão `manifests/default.pp`.

O arquivo manifesto conterá a configuração necessária do Puppet, por exemplo:

{% highlight ruby %}
# Manifesto Puppet básico para Apache

class apache {
  exec { 'apt-get update':
    command => '/usr/bin/apt-get update'
  }

  package { "apache2":
    ensure => present,
  }

  service { "apache2":
    ensure => running,
    require => Package["apache2"],
  }
}

include apache
{% endhighlight %}

Aí então adicionamos no Vagrantfile o suporte ao provisionamento Puppet:

{% highlight ruby %}
Vagrant::Config.run do |config|
  config.vm.box = "lucid32"

  # Habilita o provisionador Puppet
  config.vm.provision :puppet
end
{% endhighlight %}

Alternativamente você pode executar o Puppet no modo cliente-servidor
habilitando o provisionador `:puppet_server`. Veja a documentação do
[Puppet Server](/v1/docs/provisioners/puppet_server.html) para mais detalhes.

**Observação:** O exemplo Puppet acima não é totalmente equivalente ao exemplo
com o Chef, pois o Apache não está sendo configurado adequadamente para servir
nosso diretório `/vagrant`. O principal objetivo aqui é mostrar como o
provisionamento Puppet funciona com o Vagrant. Você pode imaginar como poderia
configurar o Apache mais à frente para que ele sirva o diretório `/vagrant`.

## Executando!

Com o provisionamento configurado, apenas execute `vagrant up` para criar seu
ambiente e o Vagrant irá automaticamente provisioná-lo. Se seu ambiente já
estiver sendo executado por causa de algum `up` em um passo anterior, execute
apenas `vagrant reload`, o que irá reiniciar rapidamente sua VM, ignorando o
passo de importação.

Depois que o Vagrant completar a execução, o servidor web estará instalado e
também sendo executado. Você ainda não poderá enxergar seu site de um
navegador, pois ainda não abordamos o redirecionamento de portas, mas você pode
confirmar que o provisionamento funciona acessando por SSH sua VM e
verificando a saída no IP `127.0.0.1`:

{% highlight bash %}
$ vagrant ssh
...
vagrant@vagrantup:~$ wget -qO- 127.0.0.1
<h1>Hello from a Vagrant VM</h1>
vagrant@vagrantup:~$
{% endhighlight %}

Isso funciona porque os script para dos provisionadores acima foram escritos
para modificar o `DocumentRoot` do Apache para apontar para o seu diretório
`/vagrant`. Os detalhes exatos de como isso foi feito são específicos para
cada provisionador e estão fora do escopo e do objetivo desse guia de
iniciação. Para mais informações, recomendamos investigar sobre o Chef e o
Puppet.

No próximo passo do guia de iniciação, vamos mostrar como acessar seu site
usando seu próprio navegador.
