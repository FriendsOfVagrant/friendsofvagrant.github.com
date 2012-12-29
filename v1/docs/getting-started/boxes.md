---
layout: getting_started
title: Começando - Boxes

current: Boxes
previous: Configuração do Projeto
previous_url: /v1/docs/getting-started/setup.html
next: SSH
next_url: /v1/docs/getting-started/ssh.html
---
# Boxes

Depois da inicialização do projeto, o primeiro passo sempre é definir a
_base box_ no Vagrantfile. O Vagrant não cria uma instância de máquina virtual
_totalmente_ do zero. Em vez disso, ele importa uma imagem base para a VM e
constrói a partir dela. Isso simplifica excelentemente as coisas para os
usuários do Vagrant, pois eles não tem que perder tempo definindo detalhes
entediantes como capacidade de memória, tamanho do disco rígido, controladores
de rede etc., e também permite que sejam usadas bases personalizadas para
construir o projeto em cima delas.

As bases sobre as quais o Vagrant constrói são empacotadas como "boxes", que
são basicamente pacotes tar em um formato específico para o Vagrant. Qualquer
pessoa pode criar uma box, e o empacotamento será abordado de forma mais
específica na seção [empacotamento](/v1/docs/getting-started/packaging.html).

## Conseguindo uma Base Box

Nós já empacotamos uma base box que tem o esqueleto de uma instalação do
Ubuntu Lucid (10.04) 32-bit. Perceba que, se você já fez o download dessa box
na [página de visão geral](/v1/docs/getting-started/index.html), você não
precisa baixá-la novamente.

O Vagrant permite que se adicionem boxes tanto do sistema de arquivos local
quando de uma URL HTTP. Comece executando o seguinte comando para que ele
inicie o download enquanto abordamos a instalação da box em mais detalhes:

{% highlight bash %}
$ vagrant box add lucid32 http://files.vagrantup.com/lucid32.box
{% endhighlight %}

As boxes instaladas são globais na instalação atual do vagrant. Isso significa
que, uma vez que a box `lucid32` é adicionada, ela pode ser usada por vários
projetos ao mesmo tempo. Todo projeto usa a box apenas como _base_, assim,
depois que a VM do projeto for criada, ela pode sofrer modificações sem afetar
os outros projetos que usem a mesma box.

Perceba que a box tem um nome próprio, nesse caso "lucid32". Esse nome é usado
pelo Vagrant para referenciar aquela box desse ponto em diante. A URL é usada
apenas quando está se fazendo a adição, depois nunca mais. E o nome do arquivo
da box não tem nenhuma ligação com o nome lógico definido. É apenas uma
coincidência que o nome do arquivo e o nome lógico sejam os mesmos nesse caso.

## Removendo Boxes

Com a mesma facilidade com que elas são adicionadas, as boxes também podem ser
removidas (mas note que essa exclusão é permanente). O comando seguinte é um
exemplo de como remover uma box.

{% highlight bash %}
$ vagrant box remove my_box
{% endhighlight %}

Se você tentar executar esse comando, ele irá falhar obviamente, pois você não
adicionou ainda nenhuma box chamada "my_box" (ou, se você tiver adicionado,
peço desculpas pois você acabou de excluí-la para sempre).

Quando uma box é removida, nenhuma nova máquina virtual baseada nessa box
pode ser criada, pois ela foi excluída complementamente do sistema de
arquivos, mas as máquinas virtuais existentes que já estavam rodando
continuarão a funcionar normalmente.

## Configurando o Projeto para usar a Box

Agora que a box lucid foi adicionada com sucesso à instalação do Vagrant,
precisamos informar nosso projeto para usá-la como base. Isso é feito através
do Vagrantfile. Abra o Vagrantfile e cole o seguinte conteúdo nele. A função
do conteúdo deve ser auto-explicativa:

{% highlight ruby %}
Vagrant::Config.run do |config|
  config.vm.box = "lucid32"
end
{% endhighlight %}

## Testando a Configuração

Até agora nós apenas especificamos uma base. Nenhuma porta foi redirecionada,
nenhum provisionamento personalizado foi feito etc. Nós literalmente temos
apenas uma única linha de configuração no nosso Vagrantfile. Mesmo assim, já
temos uma máquina virtual totalmente funcional. Você pode confirmar isso
executando o comando `vagrant up`, que irá criar o ambiente. Depois de alguns
minutos, você deverá estar com uma máquina virtual sendo executada. Ainda não
fizemos o redirecionamento de nenhuma porta e também não falamos sobre o SSH,
por isso, por enquanto, você vai ter que confiar em nossa palavra que tudo
está funcionando. No fim, quando você tiver terminado de verificar a máquina
virtual, você pode destruir tudo com o comando `vagrant destroy`.

{% highlight bash %}
$ vagrant up
...
$ vagrant destroy
...
{% endhighlight %}
