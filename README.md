# Minicurso de Shell Script
![Creative Commons Attribution 4.0 International Public License](https://licensebuttons.net/l/by/4.0/80x15.png)

## Introdução
### O que é um Shell?
O shell é uma das ferramentas mais básicas de um sistema operacional. Ele é
responsável por interpretar comandos e acessar recursos como diretórios,
arquivos, executáveis e processos.

O shell não é um software em específico, existem várias implementações
diferentes com funcionalidades distintas:

* Atualmente no Windows 10, o shell padrão é o **powershell**.
* Em sistemas derivados do Unix, o **sh** e o **bash** são os shells mais
utilizados.
* Há também outras implementações menos conhecidas e mais específicas, como zsh,
fish, ksh, csh e tcsh.

Neste curso, o shell utilizado será o **bash**, pelo motivo de estar disponível
na maioria das plataformas ([inclusive no Windows](https://msdn.microsoft.com/en-us/commandline/wsl/about)).

### O que é o Shell Script?
Para interpretar os comandos, o shell se utiliza de uma linguagem própria, o
**Shell Script**. Como qualquer outra linguagem de programação, ela definirá
como os comandos, funções, operadores, fluxo de execução e variáveis irão se
comportar.

## Prática
### Acessando o Shell
No Ubuntu, o shell pode ser acessado abrindo o Terminal.
* **Importante!** - É comum confundir **shell** com o **terminal**, porém são
duas aplicações completamente distintas. O **terminal** em si serve apenas para
renderizar a saída de texto que é produzida pelo shell ou qualquer software que
execute nele.

Ao acessar o shell nos deparamos com a mensagem de _prompt_, que precede o campo
para entrar com os comandos:

_[imagem da mensagem de prompt]_

### Comandos básicos
Os comandos à seguir estão presentes em qualquer sistema derivado do Unix, com
eles é possível interagir e navegar entre arquivos e diretórios:

| Comando    | Descrição                            |
| ---------- | ------------------------------------ |
| `ls`       | Lista o conteúdo do diretório atual  |
| `pwd`      | Mostra o caminho do diretório atual  |
| `cd`       | Navega entre diretórios              |
| `mkdir`    | Cria diretórios                      |
| `cp`       | Copia arquivos e diretórios          |
| `rm`       | Remove arquivos e diretórios         |
| `mv`       | Move arquivos e diretórios           |
| `cat`      | Mostra o conteúdo de arquivos        |

### Operadores


