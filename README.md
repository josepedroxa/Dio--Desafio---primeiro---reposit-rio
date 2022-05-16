# Dio--Desafio---primeiro---repositorio

Teste de comandos Git.

O que é o Git
O Git é o sistema opensource de controle de versão mais popular da internet.

Uma descrição mais completa é de que ele é um sistema distribuído opensourse de contre de versões.

Ele é usado principalmente no desenvolvimento de software, mas pode ser usado para registrar o histórico de edições de qualquer tipo de arquivo.

Se uma pessoa quiser controlar as versões do seu trabalho de TCC ou da monografia de doutorado, por exemplo, ela pode.

Ser opensourse significa que ele é um software livre.

Dizer que ele faz controle de versões é a mesma coisa que dizer que ele armazena conteúdo e mantém um histórico das alterações feitas nele (seja por um usuário só ou muitos).

E finalmente, dizer que ele é um sistema distribuído significa que cada diretório de trabalho do Git é um repositório com um histórico completo e habilidade total de acompanhamento das revisões, independente de acesso a uma rede ou a um servidor central.

Ou seja, cada desenvolvedor tem, na sua máquina, acesso ao histórico completo do código trabalhado.

Porque preciso dos comandos Git
É muito comum que empresas tenham mais de um dev trabalhando paralelamente no mesmo projeto. Então, em primeiro lugar, sistemas como o Git existem para o código não virar uma bagunça.

Pode haver também a necessidade de voltar para uma versão anterior, por uma série de motivos, e ter esse controle dá muito mais segurança pra quem está trabalhando.

Outro caso comum é o de equipes trabalharem paralelamente com projetos que tenham uma base de código comum. Aí a capacidade do Git de criar ramificações passa a ser bastante útil.

Como começar com comandos Git
Vou explicar utilizando o VSCode, editor que eu uso como padrão com o Git. Caso você queira saber como configurá-lo como editor padrão também, confira o link a seguir:

Visual Studio Code + Git: como transformar o VSCode no editor padrão

Para começar, vamos abrir o arquivo .gitconfig, responsável pelas opções de configuração do GIT, utilizando no terminal o comando:

git config --global -e
No arquivo de configuração, devemos encontrar a sessão Alias.

Caso essa sessão não exista no .gitconfig, realize a declaração desta nova sessão no final do arquivo, procedendo com a inclusão da expressão alias entre colchetes:

[alias]

Após a declaração da sessão, podemos proceder com a configuração de nosso primeiro atalho para os métodos do Git.

Informações dos comandos Git
Iremos criar um atalho para o comando git status, simplificando sua utilização.

Atente para o parâmetro -s no final do atalho criado, essa opção permite um status resumido, resultando em maior dinamismo.

Caso em algum momento seja necessário um status mais completo, podemos utilizar normalmente o comando: git status.

s = !git status -s
git status
comando git status 
Os commits
O segundo atalho que iremos criar será para o nosso processo de commit.

Nesta configuração utilizaremos os parâmetros –all, que adiciona todos os arquivos para o staged de mudanças, e logo em seguida (&&) executa o commit com o parâmetro -m que nos permite incluir a mensagem descritiva do nosso commit.

c = !git add --all && git commit -m
Lembre-se que caso você não queira adicionar todos os arquivos alterados para o processo de commit, deve-se incluir individualmente os arquivos que desejamos com o comando tradicional git add [nome do arquivo] e depois executarmos o comando git commit -m “[Mensagem Descritiva]”. Ou seja, o processo tradicional.

Git log
Também incluiremos o atalho para o comando git log, utilizando opções de personalização do comando, permitindo uma visualização mais amigável e descritiva.

Para isso utilizaremos o parâmetro –prety=format: que irá permitir customizarmos a apresentação de nossos logs, a partir do atalho que criarmos, com algumas opções específicas:

%h: o percentual com a letra h minúscula irá apresentar o hash reduzido do commit;
%d: o percentual com a letra d minúscula irá mostrar a branch, e também a tag caso exista, do commit;
%s: o percentual coma letra s minúscula (de subject) irá demonstrar a mensagem do commit.
%cn: nome da pessoa que realizou o commit;
%cr: a data relativa do commit.
Também utilizaremos a opção de utilizar cores diferentes para cada coluna, o que facilita a visualização, utilizado o parâmetro % com a letra C maiúscula (%C) seguido da cor que desejamos entre parênteses (blue).

l = !git log --pretty=format:'%C(blue)%h%C(red)%d %C(white)%s - %C(cyan)%cn, %C(green)%cr'
git log
Por fim, o arquivo .gitconfig ficará desta forma:

conclusão do gitconfig
Assim, concluímos a configuração dos atalhos básicos do Git que eu mais utilizo.

Encontre a oportunidade de trabalho ideal para você! Vagas para desenvolvedor com o seu perfil. Confira!

Agora que você já sabe como configurá-lo, gostaria de passar também, de forma mais geral e didática, os dez principais comandos do Git que toda pessoa desenvolvedora deveria saber. Confira!

10 Principais comandos Git
Git init
Para começar um projeto que ainda não seja um repositório (ou repo), o Git Init costuma ser o primeiro comando que você vai usar, pois vai precisar de um subdiretório .git na raiz do seu projeto.

Esse comando cria um repositório vazio ou transforma uma pasta que você já tem, e que não está com controle de versão, em um repositório.

git init
Com sua pasta de trabalho devidamente iniciada, é hora de começar a preenchê-la.

Git clone
O Git clone é um comando para baixar o código-fonte existente de um repositório remoto (como o Github, por exemplo).

Existem algumas maneiras de baixar o código-fonte, mas eu prefiro o clone com o modo https:

git clone <https://url-do-link>
Quando você clonar um repositório, o código é copiado para a o seu computador e continua linkado ao original, como foi explicado lá na descrição do que é um sistema distribuído.

Se você quiser desvincular a sua cópia do original, rode o comando abaixo:

git remote rm origin
Git branch
Com branches (ou ramificações), vários desenvolvedores podem trabalhar paralelamente no mesmo projeto. Assim, cada um pode codar a sua parte sem se atrapalharem.

Por isso, esse é um dos comandos Git mais importantes. Pode-se usar o comando git branch para criar, listar e excluir branches.

Criando uma nova branch:

git branch <nome-da-branch>
Este comando criará uma branch local. Para upar a nova branch para o repositório remoto, você precisa usar o seguinte comando:

git push -u <remote> <nome-da-branch>
Para ver as ramificações:

git branch 
ou
git branch --list
Deletando uma branch:

git branch -d <nome-da-branch>
Git checkout
Este é um dos comandos Git mais usados. Para trabalhar em uma branch, primeiro você precisa mudar para ela. Não ir para a branch que você acabou de criar e na qual quer trabalhar é um erro bastante comum no começo.

Então, usamos o git checkout principalmente para mudar de um branch para outro. Também podemos usá-lo para verificar arquivos e commits:

git checkout <nome-da-ramificação>
Há ainda um comando de atalho que te permite criar e ir para um branch de uma vez só:

git checkout -b <nome-da-branch>
Git status
O comando status do Git fornece algumas informações sobre a branch em que você estiver no momento, como seu nome, se ela está atualizada em relação à master e quais arquivos foram alterados.

git status
Git add
Quando criamos, modificamos ou excluímos um arquivo, essas alterações ocorrerão em nosso ambiente local e não serão incluídas no próximo commit (a menos que alteremos as configurações).

Precisamos usar o comando git add para incluir as alterações de um arquivo em nosso próximo commit.

Para adicionar apenas um arquivo:

git add <arquivo>
Para adicionar, de uma vez, todos os arquivos modificados:

git add -A
O comando git add não altera o repositório e as alterações não são salvas até usarmos o git commit.

Git commit
Este comando é como definir um ponto de verificação no processo de desenvolvimento, para o qual você pode voltar mais tarde, se necessário.

git commit -m "mensagem explicando a mudança no código"
Git push
Após confirmar as alterações, a próxima coisa que você deseja fazer é enviar as alterações para o servidor remoto.

O comando git push envia e salva suas confirmações no repositório remoto.

git push <remote> <nome-do-branch>
No entanto, se seu branch for criado recentemente, você também precisará fazer upload do branch com o seguinte comando:

git push -u origin <nome-do-branch>
Git pull
O comando git pull é usado para obter atualizações do repositório remoto. O comando de pull depende do referencial de onde ele foi feito, ou seja, um git pull feito da sua máquina vai puxar informações do repositório original para ela.

Mas um git pull feito a partir do repositório original vai puxar as informações da sua máquina. Percebe?

Este comando é uma combinação de git fetch (baixa as alterações do repositório remoto mas não mescla elas com o seu) e git merge (que mescla tudo junto), o que significa que, quando usamos o git pull, ele recebe as atualizações do repositório remoto (git fetch) e aplica imediatamente as alterações mais recentes no seu local (git merge).

git pull <remote>
Git revert
Existem várias maneiras de desfazer nossas alterações local ou remotamente (dependendo da necessidade), mas devemos usar esses comandos com cuidado para evitar problemas.

Uma maneira segura de desfazer os commits é usando git revert.

git revert 'número do hash'