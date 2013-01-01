---
layout: getting_started
title: Começando - Reconstrua Instantaneamente

current: Reconstrua Instantaneamente
previous: Desmontagem
previous_url: /v1/docs/getting-started/teardown.html
---
# Reconstrua Instantaneamente

Vamos supor que é hora de trabalhar nesse projeto web novamente. Pode ser
no dia seguinte no trabalho, ou talvez no _ano_ seguinte, mas seu chefe quer
que você trabalhe novamente naquele projeto web. Preocupado com dependências?
Ou talvez com versões incompatíveis?

Não se preocupe! Nós já construímos o ambiente de desenvolvimento para esse
projeto web com o Vagrant! Sua reconstrução é muito rápida.

**Observação** Se você estiver acompanhando e não tiver destruído
completamente seu ambiente virtual, faça isso agora rodando o
`vagrant destroy`, assim você irá experimentar realmente esse passo do
guia de iniciação.

Você está pronto? Retorne ao diretório do projeto web e execute o seguinte
comando:

{% highlight bash %}
$ vagrant up
{% endhighlight %}

**É isso _aí_!** Sério! Em apenas 5 minutos mais ou menos o Vagrant completou
a configuração do seu ambiente, que deve estar exatamente do jeito que você
se lembra: mesma configuração do servidor, mesmas versões de dependências,
nenhum software estranho etc.
