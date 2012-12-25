# [friendsofvagrant.github.com](http://friendsofvagrant.github.com)

Tradução da documentação do Vagrant para português do Brasil . O Vagrant é uma
ferramenta para criar e distribuir ambientes de desenvolvimento virtualizados.

## Contribuindo com a tradução da documentação oficial do Vagrant:

### Informando os documentos que deseja traduzir

Para melhor organização, primeiro informar o(s) documento(s) que pretende
ajudar na tradução e/ou revisão na planilha de tradutores/revisores:
https://docs.google.com/spreadsheet/ccc?key=0AjRfOAFDl97mdHN5ZVNyY0xOVkxXbG50Zy1IcG52UGc#gid=0

Se ainda não possuir acesso de edição nesta planilha, solicitar o acesso para rogeriopradoj at gmail dot com.

### Utilizando o Git e o Github

1. Para começar, fazer o fork (dar uma garfada!) do repositório master da
tradução para o português no github:

    1.1. Acessar o repositório master no github:
    https://github.com/FriendsOfVagrant/friendsofvagrant.github.com

    1.2. Clicar no botão fork

2. Agora, você irá "clonar" o projeto para a sua máquina local:
   
    2.1. Copiar a URL do repositório do seu fork, para utilizá-la com o
    comando git clone (por exemplo):
        
        $ git clone git@github.com:SeuUsername/friendsofvagrant.github.com

    2.2. Após completar o clone do repositório, ele terá o nome remoto
    "origin". Não confundir, apesar do nome ser origin ele não está apontando
    para o repo master, mas sim para o seu fork no github.

3. Pronto, agora é só trabalhar na tradução do(s) documento(s).Sempre crie um
branch para a tradução que estiver fazendo. Isso porque é sempre interessante
deixar o seu branch `master` sincronizado com o que está no repositório
principal. Exemplo de criação de branch:

    3.1. Garanta que está no branch `master`

        $ git checkout master

    3.2. Cria um branch a partir do `master`

        $ git branch nomeDoBranchQueVoceVaiCriar

    3.3. Entra no branch para começar a trabalhar

        $ git checkout nomeDoBranchQueVoceVaiCriar

4. Finalizadas as traduções e/ou revisões, faça o commit das alterações no seu
repositório local:

        $ git commit –a –m "[pt_BR] translation of some page"

5. Atualize o seu repositório no servidor github com as alterações realizadas
localmente:

        $ git push origin nomeDoBranchQueVoceVaiCriar

6. Termine fazendo um `pull request`, do seu repositório no github para o
repositório master, https://github.com/FriendsOfVagrant/friendsofvagrant.github.com.
[Ajuda?](http://help.github.com/pull-requests/)


### Mantendo seu repositório local atualizado

Sempre antes de fazer as suas alterações locais, lembrar de executar o comando
`pull` para sincronizar seu repositório local com o repositório de origem (o
qual você forkou/garfou):

    $ git remote add upstream https://github.com/FriendsOfVagrant/friendsofvagrant.github.com.git
    $ git checkout master
    $ git pull upstream master


### Padrões a serem seguidos durante a tradução

#### Mensagens dos Commits

As mensagens dos commits devem ser todas em INGLÊS e devem ter o seguinte prefixo:
`[pt_BR][assunto][arquivo]`seguido da mensagem do commit.

Ex.: Se você estiver traduzindo o arquivo ssh.md do getting-started, a mensagem do commit poderia ser semelhante a seguinte:

    [pt-br][getting-started][ssh.md]Translate into Brazilian Portuguese

Para escrever boas mensagens de commit, começe por aqui:

* [https://github.com/erlang/otp/wiki/Writing-good-commit-messages](https://github.com/erlang/otp/wiki/Writing-good-commit-messages)

* [http://rogeriopradoj.com/2011/11/29/uma-nota-sobre-as-mensagens-do-git-commit/](http://rogeriopradoj.com/2011/11/29/uma-nota-sobre-as-mensagens-do-git-commit/)

* [http://blog.augustopascutti.com/Desenvolvimento/2012/07/17/Commit-messages.html](http://blog.augustopascutti.com/Desenvolvimento/2012/07/17/Commit-messages.html)

#### Formato da documentação

A documentação do Vagrant utiliza a linguagem [Markdown](http://daringfireball.net/projects/markdown/)
juntamente com o [Jekyll](http://jekyllrb.com/).

Para testar se a documentação está ok na sua máquina, depois de instalar o
Jekyll, faça o seguinte:
    
    $ cd CaminhoParaSeuRepositorioLocal
    $ jekyll --server

A documentação vai ficar disponível na url [http://localhost:4000](http://localhost:4000).

### Referências

* SSH issues: Guia contendo as soluções para os problemas mais comuns
  referentes a conexão SSH no GitHub (chave pública, ...): [http://help.github.com/ssh-issues/](http://help.github.com/ssh-issues/)

* Mencionar alguém em um ``pull request`` ou ``issue``: [https://github.com/blog/1004-mention-autocompletion](https://github.com/blog/1004-mention-autocompletion)