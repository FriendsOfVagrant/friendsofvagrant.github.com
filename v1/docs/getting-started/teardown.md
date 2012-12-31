---
layout: getting_started
title: Começando - Desmontagem

current: Desmontagem
previous: Empacotamento
previous_url: /v1/docs/getting-started/packaging.html
next: Reconstrua Instantaneamente
next_url: /v1/docs/getting-started/rebuild.html
---
# Desmontagem

Agora nós temos uma máquina virtual totalmente funcional que pode ser usada
para desenvolvimento web básico. Nós empacotamos a máquina virtual e a
repassamos para outros outros membros da equipe. Mas agora, vamos dizer que
chegou a hora de mudar de ares, talvez trabalhar em outro projeto ou ir
almoçar ou talvez ir para casa. O que faremos para limpar nosso ambiente
de desenvolvimento?

Existem três opções para limpar seu ambiente:

1. Suspender
1. Parar
1. Destruir

Cada uma dessas opções tem seus prós e contras, que serão abordados abaixo.

## Suspender o Ambiente

Uma opção é _suspender a máquina virtual_ executando `vagrant suspend`. Isso
irá salvar o estado de execução atual de sua máquina virtual e então pará-la.
Para retomar o trabalho novamente em algum momento, execute para isso apenas
um `vagrant resume`.

O maior benefício disso é que a retomada do seu trabalho é rápida, questão
de 10 a 15 segundos. O custo é que seu espaço em disco continua a ser
consumido pela máquina virtual. Uma máquina virtual média usa por volta de
1 GB do espaço em disco.

## Parar o Ambiente

Outra opção é _para a máquina virtual_ executando `vagrant halt`. Ele tentará
fazer um desligamento normal na sua VM (como se estivesse rodando um `halt`
numa máquina linux) e esperar que ela seja desligada. Para retomar o trabalho,
rode um `vagrant up` que irá reinicar a máquina mas não repetirá a sequência
de importação (uma vez que ela já foi importada antes).

O maior benefício disso é que ele permite que se desligue de forma limpa sua VM,
e a traz com um estado inicial novamente. O custo é que você ainda precisará
pagar pelo espaço em disco que é consumido pela máquina virtual.

## Destruir o Ambiente

Por fim, você pode _destruir completamente seu ambiente virtual_. Isso pode
ser feito executando o `vagrant destroy` que irá apagar literalmente todos os
rastros da máquina virtual do disco. Para voltar ao trabalho novamente,
execute o `vagrant up` e seu ambiente será reconstruído.

O benefício disso é que seu espaço em disco é restaurado completamente ao
estado pré-VM, economizando por volta de 1 GB em média. O custo é que você
precisará esperar por uma reconstrução completa quando rodar o `vagrant up`
novamente.

Geralmente você não destruiria o ambiente de um projeto ativo, a menos que
o espaço em disco for realmente um problema. Em vez disso, a maioria dos
usuários escolhe suspender ou parar seus projetos.
