(arvore-de-diretorios)=

# Árvore de diretórios do Ubuntu

- Traduzido de: <http://doc.ubuntu-fr.org/arborescence>
- Tradutor: Jurandy Soares
- Data da tradução: 05/jan/2021

O Ubuntu adere à [hierarquia padrão do sistema de arquivos](http://www.pathname.com/fhs/) ( *Filesystems Hierarchy Standard*, FHS), que define o nome, a função e a árvore de arquivos e diretórios em um sistema de arquivos.

Facilita a localização de diretórios e arquivos para usuários e desenvolvedores de software.


## Geral

### Como uma árvore

```{figure} imagens/arborescence-nautilus.png
:name: figura:diretorios
:align: center
-- Árvore de diretórios no Nautilus
```

Compare o armazenamento de diretórios e arquivos em seu computador com uma árvore (Veja {numref}`figura:diretorios`): começando pela raiz de uma árvore, movendo seu dedo ao longo da árvore, seguindo o tronco e depois os galhos, você pode tocar em qualquer folha desta árvore.

```{figure} imagens/arv-dir-bottomtop.png
:name: figura:arvore-bt
:align: center
-- Árvore de diretórios com raiz (`/`) embaixo
```

Uma árvore na natureza possui sua raiz na parte de baixo. Poderíamos representar a árvore de diretórios do Linux conforme representado na {numref}`figura:arvore-bt`. No entanto, isso não seria intuitivo, pois a árvore de diretórios representa uma hierarquia de diretórios (pastas) com etiquetas (nomes) e nós ocidentais lemos da esquerda para a direita. Por esta razão, a árvore de diretórios é comumente representada com a raiz à esquerda, semelhante ao observado na {numref}`figura:arvore-lr`.

```{figure} imagens/arv-dir-leftright.png
:name: figura:arvore-lr
:align: center
-- Árvore de diretórios com raiz (`/`) à esquerda
```

Em sistemas do tipo {abbr}`GNU (GNU Não é Unix)`/Linux, todas as informações armazenadas em sua mídia de armazenamento (discos rígidos, pendrives , cartões SD, CD-ROMs, etc.) são necessariamente acessíveis seguindo um caminho a partir de um local lógico chamado a raiz (indicada por uma barra simples: `/`).

A raiz simboliza uma partição que você define como base para armazenar seus arquivos. Em seguida, essa base é separada (como ramos de uma árvore) logicamente em diretórios (pastas), eles próprios separados em subdiretórios e subdiretórios, etc. em que seus arquivos são salvos (simbolicamente, as folhas da árvore).

### Exemplos básicos

| Descrição                                             | Caminho                                            |
| ----------------------------------------------------- | -------------------------------------------------- |
| Pasta raiz                                            | `/`                                                |
| Pasta de dispositivos de armazenamento USB removíveis | `/media/USUARIO/ETIQUETA`                          |
| Pasta base do usuário                                 | `/home/USUARIO` ou `~`                             |
| Dados de seus aplicativos                             | `/home/USUARIO/.local/share/` ou `~/.local/share/` |

## O padrão de acordo com o FHS

O *Filesystem Hierarchy Standard* define uma organização padrão para esses diretórios. Portanto, não importa qual distribuição GNU/Linux (ou qualquer outro sistema operacional aderente a esse padrão) você esteja usando, você será capaz de encontrar as informações que procura.

```{toctree}
:maxdepth: 1

fhs/01-barra.md
fhs/02-barra_bin.md
fhs/03-barra_boot.md
fhs/04-barra_dev.md
fhs/05-barra_etc.md
fhs/06-barra_home.md
fhs/07-barra_lib.md
fhs/08-barra_media.md
fhs/09-barra_mnt.md
fhs/10-barra_opt.md
fhs/11-barra_proc.md
fhs/12-barra_root.md
fhs/13-barra_run.md
fhs/14-barra_sbin.md
fhs/15-barra_srv.md
fhs/16-barra_tmp.md
fhs/17-barra_usr.md
fhs/18-barra_usr_bin.md
fhs/19-barra_usr_lib.md
fhs/20-barra_usr_local.md
fhs/21-barra_usr_share.md
fhs/22-barra_var.md
```

### Considerações avançadas

A seguir está uma lista de considerações importantes quando se trata de diretórios e partições. Observe que o uso do disco varia muito, dependendo da configuração do sistema e dos padrões de uso específicos. As recomendações aqui são diretrizes gerais e fornecem um ponto de partida para o particionamento.

```{warning}
O tamanho mínimo ou recomendado de cada partição muda de acordo com a distribuição do Linux ou com as aplicações em execução. Por exemplo, desde o [Marco civil da internet no Brasil](http://www.planalto.gov.br/ccivil_03/_ato2011-2014/2014/lei/l12965.htm) um espaço maior deve ser dedicado à partição `/var` para possibilitar o armazenamento e rotação de logs de dados.
```

- `/` (a raiz): deve sempre conter fisicamente `/etc` , `/bin` , `/sbin` , `/lib` e `/dev` , caso contrário, você não será capaz de inicializar o sistema. Normalmente, são necessários [25 GB para instalação do Ubuntu Desktop](https://help.ubuntu.com/community/Installation/SystemRequirements).
- `/usr`: contém todos os programas do usuário (`/usr/bin`), bibliotecas (`/usr/lib`), documentação (`/usr/share/doc`), etc. Esta é a parte do sistema que geralmente ocupa mais espaço em disco. Você deve reservar pelo menos 10 GB. Este espaço deve ser aumentado dependendo do número e tipo de pacotes que você pretende instalar. Uma instalação padrão do Ubuntu aqui requer um mínimo de 7 GB. Uma estação de trabalho ou servidor deve permitir de 7 a 10 GB.
- `/var`: dados variáveis, como artigos, e-mails, sites, bancos de dados, cache do gerenciador de pacotes, etc. será colocado neste diretório. O tamanho desse diretório é altamente dependente do uso do sistema, mas para a maioria das pessoas, ele será ditado pelo consumo geral do gerenciador de pacotes. Se você estiver fazendo uma instalação completa de quase tudo que o Ubuntu tem a oferecer, tudo em uma sessão, reservar de 2 a 3 GB de espaço para `/var` deve ser suficiente. Se você instalar em partes (passo a passo, pouco a pouco), de 300 a 500 MB serão suficientes. Se o espaço no disco rígido for crítico e você não estiver planejando fazer atualizações importantes, pode atualizar de 30 a 40 MiB.
- `/tmp`: Dados temporários criados por programas provavelmente irão para este diretório. De 1 GB a 2 GB geralmente são suficientes. Alguns aplicativos -- incluindo manipuladores de arquivo, ferramentas de gravação e software de multimídia -- podem usar `/tmp` temporariamente para armazenar arquivos de imagem. Se você planeja usar esses aplicativos, deve ajustar o espaço em disco de acordo.
- `/home`: Cada usuário colocará seus dados pessoais em um subdiretório desse diretório. Seu tamanho depende de como os usuários usarão o sistema e quais arquivos serão armazenados em seu diretório. Dependendo do que você planeja fazer com seu computador, você deve reservar cerca de 1 GB para cada usuário. Mas adapte esse valor às suas necessidades pessoais. Reserve muito mais espaço se você planeja salvar muitos arquivos de mídia (fotos, músicas, vídeos) em seu diretório inicial ou criar máquinas virtuais. É neste diretório que se encontram os arquivos de configuração de cada programa, tradicionalmente sob o nome `/home/NOME_USUÁRIO/.NOME_PROGRAMA` (Ex: `~/.thunderbird` para o Thunderbird). Você notará que todos os arquivos começam com um ponto, ou seja, estão {ref}`ocultos`.

## Veja também

- {ref}`fhs`
- {ref}`caminhos`























