(pacote)=

# Pacote de software

- Traduzido de: <https://doc.ubuntu-fr.org/paquet>
- Tradutor: Jurandy Soares
- Data da tradução: 06/jan/2021

![Ícone de pacote .deb](imagens/deb.png)

Um pacote de software refere-se ao software contido em um arquivo que, manipulado por um sistema de gerenciamento de pacote de software, instala ou remove o software em questão de um computador.

Mais precisamente, um pacote contém os arquivos, no todo ou em parte, de um software ou de uma biblioteca de componentes dentro do mesmo arquivo compactado. Este arquivo também [contém scripts de instalação](https://pc.oulu.ifrn.edu.br/var/lib/dpkg/info/), instruções que são compreendidas por um sistema de gerenciamento de pacotes e que permitem colocar o software ou arquivos de biblioteca no local apropriado na árvore do sistema de arquivos. Esses mesmos scripts de instalação podem ser lidos ao contrário pelo sistema de gerenciamento de pacotes para remover completamente o software instalado.

Um pacote, sozinho, está incompleto. Deve ser manuseado por um gerenciador de pacotes , o sistema possibilitando processar (instalar, atualizar, validar e deletar) pacotes de software.

## Pacotes de software no Ubuntu

Os pacotes de software compatíveis com o sistema operacional Ubuntu são aqueles distribuídos no formato Debian (`.deb`). Eles são recuperáveis ​​de várias maneiras:

- por meio de [repositórios de pacotes de software oficiais e não oficiais](https://sempreupdate.com.br/o-que-sao-quais-sao-repositorios-do-ubuntu-como-habilitar-ou-desabilitar/);
- através de [repositórios de pacotes de software pessoais](https://diolinux.com.br/linux/linux-mint/como-adicionar-um-ppa-no-ubuntu.html) ([Personal Packages Archive , PPA](https://launchpad.net/ubuntu/+ppas));
- de um CD-ROM ou DVD-ROM do Ubuntu , ou mídia de compilação de pacote para o Ubuntu ;
- dos sites oficiais dos fornecedores de software. Exemplos:
  - [Google Chrome](https://dl.google.com/linux/direct/google-chrome-stable_current_amd64.deb)
  - [VirtualBox](https://www.virtualbox.org/wiki/Linux_Downloads)

Os pacotes [flatpak](https://flatpak.org/) e [snap](https://snapcraft.io/) também podem ser usados ​​em um sistema Ubuntu, embora suas operações sejam diferentes.

## Scripts para os pacotes

Nas distribuições Debian e derivados, o diretório `/var/lib/dpkg/info/` armazena vários arquivos com dados sobre os pacotes instalados em seu sistema. Visite-o (Execute: `cd /var/lib/dpkg/info/`)  para ver:
- Lista de arquivos de configuração (Execute: `ls *.conffiles`)
- Lista dos arquivos implantados (Execute: `ls *.list`)
- Gatilhos (Execute: `ls *.triggers`)
- Soma de verificação (*checksum* em inglês) para alguns arquivos (Execute: `ls *.md5sums`)
- Scripts de:
  - Configuração (Execute: `ls *.config`)
  - Pré-instalação (Execute: `ls *.preinst`)
  - Pós-instalação (Execute: `ls *.postinst`)
  - Pré-remoção (Execute: `ls *.prerm`)
  - Pós-remoção (Execute: `ls *.postrm`)

Vejamos o exemplo do pacote que instalou o agendador de tarefas **cron**:

  cd /var/lib/dpkg/info
  ls cron.*

Escolha um dos arquivos que você deseja visualizar e use um comando ou 
ferramenta para visualização do arquivo escolhido: 
- `cat -n ARQUIVO`
- `less ARQUIVO` (Pressione `q` para sair)
- `nano -v ARQUIVO` (Pressione {kbd}`Ctrl+X` para sair)
- `view ARQUIVO` (Pressione {kbd}`Esc:`, depois digite `q!`, e pressione {kbd}`Enter` para sair)
- `batcat ARQUIVO` (Pressione `q` para sair)
- `code ARQUIVO`  (Somente se você estiver no ambiente Desktop)
- `gedit ARQUIVO`  (Somente se você estiver no ambiente Desktop)


## Referências

- [ubuntu - friendly-recovery is broken, keeps returning exit status 1 - Super User](https://superuser.com/questions/1356284/friendly-recovery-is-broken-keeps-returning-exit-status-1)
- [6. Package maintainer scripts and installation procedure — Debian Policy Manual v4.5.1.0](https://www.debian.org/doc/debian-policy/ch-maintainerscripts.html)
