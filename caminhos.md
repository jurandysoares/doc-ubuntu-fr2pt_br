(caminhos)=

# Caminhos de acesso no Linux

- Traduzido de: <http://doc.ubuntu-fr.org/chemins>
- Tradutor: Jurandy Soares
- Data da tradução: 18/dez/2020

Na computação, o conteúdo geralmente é armazenado em arquivos.

Como esses são rapidamente muito numerosos, para se orientar, projetamos os sistemas de arquivos como estruturas em árvore: os arquivos são armazenados em diretórios e, além dos arquivos, cada um desses diretórios pode conter vários outros diretórios.

A referência a um recurso (arquivo ou diretório) é chamada de caminho de acesso (em inglês: *path*). Nesse caminho, no Linux, os nomes dos diretórios e de qualquer arquivo são separados por uma barra `/` (enquanto uma barra invertida `\` é usada no Windows).

Existem dois tipos de caminho: absoluto e relativo .

## Caminho absoluto

Um caminho absoluto é baseado na raiz da árvore e começa com `/`, por exemplo: /home/usuario/<pasta>/<arquivo>. Ele permanece válido em qualquer contexto (desde que ainda esteja no mesmo sistema da mesma máquina).

```{tip}
`/` logo no início de um caminho é, portanto, aproximadamente o equivalente ao `C:\` no Windows 
```

## Caminho relativo

Um caminho relativo é a priori relativo ao diretório atual onde o usuário está localizado. Um caminho que começa com algo diferente de `/` ou `~` é um caminho relativo. Esta noção de posicionamento depende do contexto, mas no Linux você geralmente é encontrado por padrão em seu diretório pessoal, que é `/home/<nome do usuário>`. Em um terminal, você pode navegar de um diretório para outro com o comando `cd`.

Este tipo de caminho também pode ser usado para indicar onde os recursos estão localizados em relação uns aos outros, independente da raiz do sistema, por exemplo, para os arquivos de um servidor web que podem ser movidos juntos possam se encontrar.

## Links

Podemos usar links físicos ou simbólicos para criar, por exemplo. atalhos entre caminhos diferentes.

Em particular, `.` é usado como um nome de diretório indica o diretório atual e `..` indica o diretório pai (esses são links físicos).

## Atalhos de shell

Til `~` usado como o primeiro nome de diretório substitui o caminho absoluto para seu diretório inicial `/home/usuario` (consulte [Expansão do Til](http://www.gnu.org/software/bash/manual/html_node/Tilde-Expansion.html)), mas essa funcionalidade é específica do shell , e não do sistema de arquivos.

## Recursos ocultos

Um recurso (arquivo ou diretório) cujo nome começa com `.` é um recurso oculto (portanto, não podemos listá-lo por padrão).

Com o comando `ls`, você deve adicionar a opção *a* (para <i><b>a</b>ll</i>, todos em Inglês) para listar esses recursos, o que dá:

    ls -a

Normalmente, eles também podem ser exibidos com um gerenciador de arquivos gráfico (por padrão no Ubuntu: GNOME Arquivos -- anteriormente Nautilus) com o atalho {kbd}`Ctrl+h` (para <i><b>h</b>idden</i>, "escondido" em Inglês).

```{admonition}
Em particular, existem muitos recursos ocultos em seu diretório pessoal. A ideia é ocultar aqui os diretórios e arquivos utilizados pelo sistema, mas específicos do usuário, para dar melhor visibilidade aos documentos ou conteúdos de mídia do usuário.
```

Em particular, existem muitos recursos ocultos em seu diretório pessoal. A ideia é ocultar aqui os diretórios e arquivos utilizados pelo sistema, mas específicos do usuário, para dar melhor visibilidade ao documento ou conteúdo de mídia do usuário.
Inodes
Para ir mais longe, você deve saber que cada caminho para um diretório ou arquivo é na verdade um link físico e que cada um desses links aponta para um inode que descreve o próprio recurso no sistema de arquivos. O inode descreve, entre outras coisas, as permissões , o proprietário e as datas de criação e modificação do recurso.

Veja esta página da Wikipedia para mais detalhes.

Veja também
Árvore de diretório do Ubuntu
Console: linha de comando
Sistemas de arquivos em Linux
Links físicos e simbólicos