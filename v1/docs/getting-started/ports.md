---
layout: getting_started
title: Começando - Redirecionamento de Portas

current: Redirecionamento de Portas
previous: Provisionamento
previous_url: /v1/docs/getting-started/provisioning.html
next: Empacotamento
next_url: /v1/docs/getting-started/packaging.html
---
# Redirecionamento de Portas

Nesse ponto nós temos um ambiente virtual sendo executado com o Apache
servindo um projeto web básico. Mas até agora nós só podemos acessá-lo de
dentro da VM, usando a linha de comando. O objetivo do Vagrant é fornecer
o benefício de um ambiente virtualizado sem atrapalhar suas atividades. Para
acessar seu projeto, o Vagrant possuiu uma função conhecida como
redirecionamento de portas.

O redirecionamento de portas permite que você especifique na máquina guest
portas para serem redirecionadas para a máquina host. Isso permite que você
acesse seus web services usando seu próprio navegador da sua máquina enquanto
o servidor é executado realmente dentro na máquina virtual.

## Especificando uma Porta Redirecionada

No nosso caso, queremos redirecionar apenas o Apache. O redirecionamento
da porta é especificado no Vagrantfile da seguinte forma:

{% highlight ruby %}
Vagrant::Config.run do |config|
  # Redireciona a porta 80 do guest para a porta 4567 do host
  config.vm.forward_port 80, 4567
end
{% endhighlight %}

`forward_port` é um método que recebe dois argumentos:

* **guest port** - A porta na máquina virtual.
* **host port** - A porta na máquina local que você quer usar para acessar
  a porta guest.

## Aplicando as Portas Redirecionadas

As portas redirecionadas são aplicadas durante o `vagrant up` como qualquer
outra configuração. Mas se você já estiver rodando um sistema, chamar o
`vagrant reload` irá aplicar os redirecionamentos sem ter que reimportar ou
reconstruir tudo.

Observe que o redirecionamento de portas precisa de um reinício da máquina
virtual, uma vez que o VirtualBox não aplica o redirecionamento até que
ele seja completamente reiniciado.

## Resultados!

Depois de executar o `vagrant up`, você deve conseguir acessar com seu bom e
velho navegador o endereço `localhost:4567` e enxergar a página index que
criamos anteriormente. Nesse ponto, temos uma VM totalmente funcional pronta
para desenvolvimento de um site HTML básico. Deve estar claro que se o PHP, ou
o Rails etc. tivessem sido configurados, você também poderia estar
desenvolvendo com essas tecnologias.

Por diversão, você também pode editar o arquivo `index.html`, salvá-lo,
atualizar seu navegador e imediatamente enxergar suas alterações sendo
servidas diretamente da sua VM.
