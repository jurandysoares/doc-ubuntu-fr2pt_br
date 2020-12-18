(direitos)=

# Direitos de acesso no Linux: gerenciar acesso a arquivos

- Traduzido de: <https://doc.ubuntu-fr.org/droits>
- Tradutor: Jurandy Soares
- Data da tradução: 18/dez/2020

Os sistemas operacionais inspirados no Unix (dos quais o Linux faz parte) têm a capacidade de definir de forma detalhada a gestão dos direitos de acesso aos vários arquivos do seu {term}`SO`.

Os direitos de acesso definem a propriedade de um arquivo ou diretório a um usuário e grupo de usuários. Eles também gerenciam quais ações os usuários têm permissão para executar nos arquivos, dependendo se eles são o proprietário do arquivo, um membro do grupo que possui o arquivo ou nenhum dos dois. A propriedade e o gerenciamento das permissões associadas são feitos individualmente em cada arquivo.

Este artigo é um documento explicativo sobre direitos de acesso. As seções [Os proprietários](os-proprietarios) e [As permissões](as-permissoes) apresentam de forma geral quais são esses atributos que você terá que encarar em sua vida como administrador de um sistema Linux.

A manipulação dos direitos de acesso de arquivos e pastas é discutida no artigo {ref} `Permissões <permissoes>`.

(os-proprietarios)=

## Os proprietários

Pela propriedade de um arquivo, designamos a qual usuário pertence o arquivo, quem o possui. A partir dessa posse (ou não), será possível definir as permissões de acesso ao arquivo.

A propriedade de um arquivo é definida em três categorias:

1. o **usuário proprietário** do arquivo **(u)**. Geralmente é o criador do arquivo. (Observe que um arquivo criado por um comando executado via `sudo` pertencerá ao usuário root; pode ser necessário alterar o proprietário desse arquivo para poder usá-lo com sua própria conta de usuário.)

2. o **grupo dono** do arquivo **(g)**. Se um usuário for membro de um determinado grupo que possui a propriedade de um arquivo, o usuário também terá certas permissões específicas nesse arquivo.

3. os **outros**, ou o resto do mundo **(o)**. Resumindo, todos que não são proprietários do arquivo nem membros do grupo que possui o arquivo.

Vamos fazer uma analogia com os carros. O *proprietário* seria a pessoa em cujo nome o carro está registrado. O *grupo proprietário* são todas as pessoas que estão registradas como motoristas secundários do carro na seguradora. Por fim, os restantes correspondem a todas as outras pessoas que não sejam titulares da matrícula nem inscritas como condutores do automóvel na seguradora.

```{note}
Alguns softwares precisam ser capazes de gravar em arquivos específicos para funcionar corretamente, e esse acesso é permitido dependendo se o usuário está ou não incluído em um grupo específico de membros. Este é o caso entre outros (mas não exclusivamente) do [Virtualbox](virtualbox.md) e [Wireshark](wireshark.md). Para saber como gerenciar a inclusão ou exclusão de um usuário de um grupo de usuários, consulte o documento que trata do gerenciamento de contas de usuário no Ubuntu.
```

(as-permissoes)=

## As permissões

As permissões referem-se a qual categoria de usuários (proprietário do arquivo, membros do grupo proprietário do arquivo e o resto do mundo) podem fazer em um determinado arquivo. Por exemplo, uma categoria de usuários pode ter acesso de leitura e escrita a um arquivo, enquanto outra categoria tem acesso somente leitura ao mesmo arquivo.

As permissões são definidas em três níveis:

1. a **leitura** de um arquivo: esta permissão é necessária para acessar o conteúdo de um arquivo (ouvir áudio, assistir a um filme, ler um texto, listar o conteúdo (`ls`), navegar dentro de um diretório... ). Esta permissão é conhecida por `r` (para *read*, ler em Inglês).
2. a **escrita** em um arquivo: esta permissão é necessária para fazer alterações em um arquivo (corrigir o texto e salvar as alterações; excluir "olhos vermelhos" em uma imagem e salvar a correção; adicionar, editar, renomear ou excluir um arquivo em uma pasta; etc.). Esta permissão é conhecida por `w` (para *write*, escrever em Inglês).
3. a **execução** de um arquivo: esta permissão é necessária especialmente para software, para que possam ser executados. Esta permissão é conhecida como `x`(para *eXecute*, executar em Inglês). Para um diretório, a permissão `x` permite torná-lo o diretório atual (`cd`).

Por exemplo, o usuário *toto* tem permissão de leitura e execução no diretório *foo*, mas não permissão de escrita nesse diretório; *toto* pode, portanto, executar os programas neste diretório e abrir os arquivos que ele contém, mas não pode modificá-los ou criar novos.

Para cada uma das três categorias de usuários (proprietário, membros do grupo proprietário e resto do mundo) são definidas essas três permissões:

- se o proprietário tem ou não permissão de leitura, escrita e execução em um arquivo;
- se o membro do grupo proprietário tem ou não permissão de leitura, escrita e execução em um arquivo;
- todos os outros usuários podem ou não ter permissão de leitura, escrita e execução em um arquivo.
  
Os direitos são apresentados por uma série de 9 caracteres, associados 3 a 3 (rwx rwx rwx) que definem os direitos das 3 identidades (**u**, **g** e **o**).

```{note} Diretórios: um caso especial 
O diretórios são um caso especial. Para acessar o conteúdo de um diretório (para abrir um arquivo ou mover para um subdiretório), um usuário deve ter permissão de execução (`x`) nesse diretório. Além disso, para poder listar o conteúdo de um diretório, o usuário deve ter permissão de leitura (`r`) nesse diretório. Para escrever no diretório, deve ser concedida permissão para escrever (`w`). O usuário pode ter essas permissões dependendo se ele é o proprietário do diretório, membro do grupo que possui o diretório ou parte do resto do mundo.

- Um usuário sem permissão de leitura ou execução não poderá acessar o conteúdo do diretório.
- Um usuário que tem apenas permissão de leitura poderá listar o conteúdo da pasta. (Por exemplo, com o comando `ls` em uma janela de terminal.) Ele não conseguirá acessar a pasta com seu navegador de arquivos.
- Um usuário com apenas permissão de execução pode abrir um diretório, mas não pode visualizar seu conteúdo. Isso é útil, por exemplo, para percorrer um diretório cujo conteúdo não deve ser listado.
- Um usuário com direitos de leitura e execução poderá listar o conteúdo de uma pasta e acessá-la com seu navegador de arquivos.
```

```{question} Como são determinados os direitos de acesso em um volume?

- **Sistemas de arquivos compatíveis com o padrão POSIX:** Por padrão, um novo sistema de arquivos é atribuído automaticamente ao usuáriorooteaogrupo deusuáriosroote os direitos aplicados a ele são aqueles da máscara de usuário padrão (veja abaixo) . Para modificar os direitos de acesso associados a um sistema de arquivos, você deve modificar os direitos de acesso de seu ponto de montagem. Por exemplo, para alterar os direitos de acesso de um volume */dev/sdb1* montado na pasta `/media/NewPartition/` , você deve fazer as alterações de direitos na pasta `/media/NewPartition/`. como se fosse algum arquivo. As alterações nos direitos de acesso são mantidas mesmo após a desmontagem do sistema de arquivos. Isso se aplica apenas a ext2, ext3, ext4, ReiserFS, Reiser4, HFS, HFS + e outros sistemas de arquivos compatíveis com POSIX.

- **Sistemas de arquivos incompatíveis com POSIX:** isso afeta principalmente os sistemas de arquivos FAT, vFAT e NTFS. Esses sistemas de arquivos não oferecem suporte a permissões de acordo com o padrão POSIX. Esses direitos são emulados por seu driver específico para montar o sistema de arquivos e não podem ser alterados enquanto o sistema de arquivos está montado. Propriedades e permissões são determinadas pelas opções de montagem passadas para o comando `mount` ou salvas no arquivo `/etc/fstab`. Para modificar os direitos de acesso de tal sistema de arquivos, é necessário desmontar o sistema de arquivos e, em seguida, remontá-lo com diferentes opções.
```

## Direitos atribuídos automaticamente a um arquivo

Quando um novo arquivo é criado, ele obtém automaticamente certos parâmetros:

1. **Proprietários:** por padrão, o proprietário de um novo arquivo é seu criador e o grupo proprietário é o grupo primário de seu criador. Por exemplo, se o usuário *toto*, cujo grupo principal é *usuarios*, criar um novo arquivo ou pasta, ele pertence a *toto:utilisateurs*;

2. **Permissões:** as permissões concedidas por padrão são aquelas determinadas por um parâmetro específico denominado máscara de usuário (ou *[user mask](https://pt.wikipedia.org/wiki/Umask)*). No Ubuntu, a máscara de usuário padrão concede permissões `rwx r-x r-x`, correspondentes a *umask=022*:
  
    - o proprietário do arquivo possui permissões de leitura, escrita e execução;
    - o grupo proprietário tem direitos de leitura e execução, mas não de escrita;
    - o resto do mundo tem direitos de leitura e execução, mas não de escrita.

A máscara de usuário padrão pode ser modificada para outra escolha:

- no console, durante a sessão atual. Isso é feito usando o comando *umask*. Qualquer novo arquivo ou pasta criado durante a sessão atual receberá os direitos conforme definidos pela máscara do usuário, mas a máscara do usuário padrão será usada novamente quando uma nova sessão do usuário for aberta;
- Adicionando no arquivo {file}`/etc/pam.d/common-session`:
  
        session    optional     pam_umask.so umask=007

Neste exemplo, *007* concede todos os direitos ao proprietário e ao grupo e nenhum aos outros. Em alguns casos, pode ser útil colocar *077* para restringir os direitos ao único proprietário. Esta nova máscara de usuário é usada mesmo após um novo início de sessão (login).

Outra solução é adicionar o comando abaixo após criar os usuários no arquivo {file}`~/.bashrc`:

    umask 007

Esta última modificação diretamente no arquivo *.bashrc* do usuário está disponível a partir do lançamento de um novo terminal para a linha de comando.

## Manipular direitos de acesso

Os direitos de acesso especificados em um arquivo ou pasta podem ser substituídos por outros direitos de acesso. Todas as operações são discutidas no documento sobre {ref} `permissões <permissoes>`.