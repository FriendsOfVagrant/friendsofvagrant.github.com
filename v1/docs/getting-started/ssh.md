---
layout: getting_started
title: Começando - SSH

current: SSH
previous: Boxes
previous_url: /v1/docs/getting-started/boxes.html
next: Provisionamento
next_url: /v1/docs/getting-started/provisioning.html
---
# SSH

Apesar do Vagrant permitir uma grande quantidade de configurações através de
seus comandos e do Vagrantfile, nada supera o poder da linha de comando.
Algumas vezes você tem que ir direto nos arquivos e brincar um pouco para
fazer tudo funcionar do jeito certo ou então para depurar uma aplicação.

O Vagrant fornece acesso SSH completo aos ambientes virtuais por meio de um
único comando: `vagrant ssh`. Executando `vagrant ssh`, o Vagrant irá te
mostrar automaticamente um terminal shell funcional (ele é realmente o `ssh`
sendo executado, não tem nenhum intermediário na comunicação entre a VM e a
máquina hospedeira).

Depois de rodar `vagrant ssh`, você deve enxergar algo similar ao seguinte:

{% highlight bash %}
$ vagrant ssh
...
vagrant@vagrantup:~$
{% endhighlight %}

<div class="alert alert-block alert-notice">
  <h3>Usando o Microsoft Windows?</h3>
  <p>
    Um cliente SSH em geral não é distribuído com o Windows por padrão. Por
    isso, se você estiver no Windows, o Vagrant irá disponibilizar a
    informação de autenticação SSH para que você possa usar com o seu cliente
    SSH favorito, como o
    <a href="http://www.chiark.greenend.org.uk/~sgtatham/putty/">PuTTY</a>.
  </p>
  <p>
    O Putty pode não reconhecer como válida a <code>insecure_private_key</code>
    fornecida pelo vagrant. Para consertar isso, primeiro instale o
    <a href="http://www.chiark.greenend.org.uk/~sgtatham/putty/download.html">
    PuTTYgen app</a>. Aí você irá utilizá-lo para importar a 
    <code>insecure_private_key</code>(ela fica no diretório .vagrant.d no seu
    diretório pessoal) e salvar um arquivo ppk a partir da chave privada. Use
    o arquivo ppk em vez do modo padrão para conectar via SSH na sua box
    vagrant.
  </p>
</div>

## Acessando os Arquivos do Projeto

O Vagrant liga sua aplicação com o ambiente virtual por meio de uma pasta
compartilhada do VirtualBox. A localização da pasta compartilhada na máquina
virtual por padrão é `/vagrant`, mas pode ser alterada. Essa ligação pode ser
verificada listando os arquivos dessa pasta na sessão SSH:

{% highlight bash %}
vagrant@vagrantbase:~$ ls /vagrant
index.html Vagrantfile
{% endhighlight %}

A VM tem acesso tanto de leitura quanto de escrita na pasta compartilhada.

**Lembre-se: Qualquer mudança reflete em ambos os sistemas.**
