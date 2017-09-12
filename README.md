# Minicurso de Shell Script
![Creative Commons Attribution 4.0 International Public License](https://licensebuttons.net/l/by/4.0/80x15.png)

## O que é um Shell?
O shell é uma das ferramentas mais básicas de um sistema operacional. Ele é
responsável por interpretar comandos e acessar recursos como diretórios,
arquivos, executáveis e processos.

O shell não é um software em específico, existem várias implementações
diferentes com funcionalidades distintas.

Em sistemas derivados do Unix, o *sh* e o *bash* são os shells mais
utilizados. Há também outras implementações menos conhecidas e mais específicas,
como *zsh*, *fish*, *ksh*, *csh* e *tcsh*. Todos estes podem ser generalizados
pelo termo **Unix Shells**.

Neste curso, o shell utilizado será o **bash**, pelo motivo de estar disponível
na maioria das plataformas ([inclusive no Windows](https://msdn.microsoft.com/en-us/commandline/wsl/about)).

## O que é o Shell Script?
Da mesma maneira que o shell pode interpretar comandos que o usuário digita
interativamente no terminal, é possível desenvolver scripts para realizar
tarefas mais complexas, esses scripts acabamos chamando de **scripts em shell**.
Como qualquer outra linguagem de programação, o shell definirá como os comandos,
funções, operadores, fluxo de execução e variáveis irão se comportar.

## Acessando o Shell
No Ubuntu, o shell pode ser acessado abrindo o Terminal.
* **Importante!** - É comum confundir **shell** com o **terminal**, porém são
duas aplicações completamente distintas. O **terminal** em si serve apenas para
renderizar a saída de texto que é produzida pelo shell ou qualquer software que
execute nele.

Ao acessar o shell nos deparamos com a mensagem de _prompt_, que precede o campo
para entrar com os comandos:

![prompt](https://i.imgur.com/H53X4VF.png)

## Comandos
O shell faz o trabalho de mapear e disponibilizar os comandos disponíveis do
sistema operacional, estes comandos podem ser:
* Aplicações executáveis (mapeadas pela variável de ambiente `PATH`, que veremos a seguir)
* Funções internas do shell (_builtins_)
* Funções criadas pelo usuário
* _Aliases_
* _Keywords_

Para verificar se um determinado comando existe e pra ver o tipo dele, utilize o
comando `type`:

```
user@debian:~$ type echo
echo is a shell builtin

user@debian:~$ type man
man is /usr/bin/man

user@debian:~$ type type
type is a shell builtin
```
No exemplo acima, `man` é um binário executável que está no diretório
`/usr/bin`, enquanto `type` e `echo` são funções _builtins_ do shell.

### Comandos básicos
Os comandos a seguir estão presentes em qualquer sistema derivado do Unix, com
eles é possível interagir e navegar entre arquivos e diretórios e ter acesso a
informações básicas:

| Comando    | Descrição                                        |
| ---------- | -------------------------------------------------|
| `ls`       | Lista o conteúdo do diretório atual              |
| `cd`       | Navega entre diretórios                          |
| `mkdir`    | Cria diretórios                                  |
| `cp`       | Copia arquivos e diretórios                      |
| `rm`       | Remove arquivos e diretórios                     |
| `mv`       | Move arquivos e diretórios                       |
| `cat`      | Mostra o conteúdo de arquivos                    |
| `pwd`      | Mostra o caminho do diretório atual              |
| `echo`     | Imprime mensagem de texto                        |
| `whoami`   | Mostra o nome do usuário atual                   |
| `uname`    | Mostra informações do sistema operacional        |
| `man`      | Mostra o manual de referência de comandos e APIs |

Todos os comandos podem possuir **parâmetros** e **modificadores**, como por
exemplo, o comando `ls`:

```
user@debian:~$ ls
Desktop  Downloads

user@debian:~$ ls -l
drwxr-xr-x 2 user user 4096 Sep 10 17:59 Desktop
drwxr-xr-x 2 user user 4096 Sep 10 17:59 Downloads

user@debian:~$ ls -la
drwx------ 4 user user 4096 Sep 10 17:59 .
drwxr-xr-x 5 root root 4096 Sep 10 17:58 ..
-rw-r--r-- 1 user user   21 Feb 14  2017 .bash_logout
-rw-r--r-- 1 user user   57 Feb 14  2017 .bash_profile
-rw-r--r-- 1 user user  141 Feb 14  2017 .bashrc
drwxr-xr-x 2 user user 4096 Sep 10 17:59 Desktop
drwxr-xr-x 2 user user 4096 Sep 10 17:59 Downloads

user@debian:~$ ls Downloads
learn-shell-script.zip
```

No exemplo acima o comando `ls` é chamado com dois modificadores diferentes, o
`l` e o `a`, nota-se que também é possível passar um diretório como
parâmetro.
* Dica: Veja o manual de referência do comando `ls` para descobrir a
finalidade dos modificadores (`-l` e `-a`) utilizados acima.

## Variáveis
Assim como linguagens imperativas, o shell também oferece variáveis, que podem
ser atribuídas e usadas da seguinte maneira:

```
user@debian:~$ assunto="shell script"

user@debian:~$ echo "Olá, vamos falar de $assunto?"
Olá, vamos falar de shell script?
```

* Note que não podem haver espaços antes ou depois do operador de atribuição (`=`), caso
contrário o shell interpretaria `assunto` como um comando, o que não é o que
desejamos.

Também é bastante útil atribuir a saída de comandos a variáveis:

```
user@debian:~$ hoje=$(date +%d/%m/%Y)

user@debian:~$ agora=`date +%H:%M`

user@debian:~$ echo "Olá, agora são $agora horas do dia $hoje."
Olá, agora são 10:12 horas do dia 11/09/2017.
```

As duas maneiras acima, utilizando `` ` ` `` e `$()` são equivalentes.

### Variáveis de Ambiente
No shell, há um conjunto de variáveis pré-definidas que são responsáveis por
passar informações relevantes a programas executados por ele. Essas variáveis
podem ser visualizadas com o comando `env`.

A definição das variáveis de ambiente dependem de quais arquivos são carregados
com a inicialização do shell. No **bash** [isso é um pouco complicado](https://askubuntu.com/a/463479),
mas se você quiser modificar ou criar uma nova variável de ambiente a nível de
usuário, provavelmente você irá querer modificar os arquivos `.profile` ou
`.bashrc`.

Há também variáveis especiais, como por exemplo o `$RANDOM`, que retorna um
número aleatório a cada chamada, o `$?`, que guarda o código de saída do último
comando e o `$$`, que guarda o ID de processo do shell.

## Redirecionamento de IO
### `stdin`, `stdout` e `stderr`
Chamamos de `stdin` a entrada padrão de dados de um processo.

Chamamos de `stdout` e `stderr` todo o texto que o processo imprime de volta
para o shell. A diferença desses dois canais é que o `stderr` é
convencionalmente utilizado para imprimir erros.

### Operadores
O redirecionamento de entrada e saída dos comandos é uma funcionalidade bastante
útil do shell script, com ela é possível manipular o fluxo da informação de uma
maneira fácil.

Os operadores que iremos utilizar são:

| Operador   | Descrição                                               |
| ---------- | --------------------------------------------------------|
| `>`        | Redirecionar `stdout` para arquivo (sobrescrever)       |
| `>>`       | Redirecionar `stdout` para arquivo (inserir no final)   |
| `\|`       | Redirecionar `stdout` como `stdin` do próximo comando   |
| `<`        | Redirecionar o arquivo com `stdin` para o comando       |
| `2>`       | Redirecionar `stderr` para arquivo (sobrescrever)       |
| `2>>`      | Redirecionar `stderr` para arquivo (inserir no final)   |
| `2>&1\|`   | Redirecionar `stderr` como `stdin` do próximo comando   |

A linha abaixo escreve no arquivo `processos.txt` a tabela atual de processos:
```
user@debian:~$ ps -aux > processos.txt
```
Se o arquivo não existir, ele será automaticamente criado no diretório atual. Se existir, seu
conteúdo será substituído pela saída do comando.

Vamos supor que esse arquivo será utilizado para algo importante, nesse caso,
podemos anotar a data no final dele para informar quando o conteúdo foi
extraído:
```
user@debian:~$ echo "Tabela extraída em $(date)" >> processos.txt
```

Vamos supor também que você quer enviar esse arquivo por e-mail, isso é
possível com:
```
user@debian:~$ mail -s "Processos" email@domain.com < processos.txt
```

Para o operador de pipe `|`, podemos utilizar o seguinte exemplo, supondo
que o arquivo `lista_de_compras.txt` seja uma lista com um tamanho considerável:
```
user@debian:~$ cat lista_de_compras.txt
Abacaxi
Arroz
Banana
Couve
...

user@debian:~$ cat lista_de_compras.txt | shuf | head -n 3
Pão
Leite
Ovo

user@debian:~$ cat lista_de_compras.txt | shuf | head -n 3
Arroz
Iogurte
Maçã
```
O que acontece acima? Neste exemplo podemos ver que 3 comandos são chamados, mas
o que eles fazem, em qual ordem?

Para ter uma ideia, procure saber o que os comandos `shuf` e `head` fazem, você
pode consultar com o comando `man`.

Experimente criar sua própria lista e testar o operador `|` (pipe) com ambos os comandos separadamente
para ver o que acontece:
```
user@debian:~$ cat lista.txt | shuf
...

user@debian:~$ cat lista.txt | head -n 3
...
```
