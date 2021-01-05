(fhs)=

# O FHS 

- Traduzido de: <http://doc.ubuntu-fr.org/fhs>
- Tradutor: Jurandy Soares
- Data da tradução: 04/jan/2021

O objetivo desta página de documentação é informá-lo sobre a árvore de diretórios dos principais sistemas Linux.

## Definição

O *Filesystem Hierarchy Standard* ("FHS") é um padrão na hierarquia do sistema GNU/Linux. Sua primeira versão data de 14 de fevereiro de 1994, e a versão atual é 3.0, de junho de 2015.

Referência completa: <https://refspecs.linuxfoundation.org/fhs.shtml>

## Estrutura de árvore

### /bin

Este diretório contém os comandos básicos para todos os usuários (`cp`, `mv`, `rm`…). Esses são os comandos necessários para iniciar o sistema.

### /boot 

(Recomenda-se partição separada.)  \
Aqui é onde os arquivos do seu carregador de boot (GRUB, por exemplo) e os kernels do Linux estão localizados.

### /dev

Links para periféricos físicos (CDs, discos rígidos, etc.), bem como periféricos virtuais (`/dev/null`, `/dev/random`).

Observe que os dispositivos físicos são nomeados como `/dev/sdXN` com `X` sendo uma letra e `N` um número:

- `/dev/sda1` representa a primeira partição (1) de seu primeiro disco rígido (a)
- `/dev/sdd6` representa a sexta partição (6) de seu quarto disco rígido (d) ...

### /etc

(edição de configurações em texto.)  \
Este é o local dos arquivos globais de configuração dos programas instalado.

### /home

(Recomenda-se partição separada.)  \
Diretório que contém as pastas do usuário no formato `/home/nome-do-usuário`.

### /lib

Diretório onde as bibliotecas do sistema estão instaladas.

### /mnt

Ponto de montagem para partições internas montadas temporariamente. As partições de discos rígidos internos geralmente são montadas aqui. Para partições externas, usaremos `/media` em seu lugar.

### /media

Equivalente a `/mnt`, mas para mídia removível/externa.

### /opt

É reservado para instalar pacotes de aplicativos extras, baixados da Internet, como o [Google Chrome](https://www.google.com/intl/pt-BR/chrome/).

Ref.:
<http://www.pathname.com/fhs/pub/fhs-2.3.html#OPTADDONAPPLICATIONSOFTWAREPACKAGES>

### /proc

Sistema de arquivos virtual apresenta informações sobre processos e outras informações de sistema em uma estrutura hierárquica semelhante a arquivos, fornecendo um método mais conveniente e padronizado para acessar dinamicamente dados de processos armazenados no núcleo do que os métodos de rastreamento tradicionais ou acesso direto à memória do núcleo. ([Wikipedia, 2020](https://pt.wikipedia.org/wiki/Procfs))

### /root

Diretório do usuário root.  \
Vazio por padrão no Ubuntu.

### /sbin

Série de executáveis ​​para administradores.

### /srv

Dados para serviços hospedados pelo sistema.  \
Por exemplo, conteúdo de um servidor web (HTTP) ou de um banco de dados.

### /tmp

(partição separada recomendada)  \
Diretório de arquivos temporários, esvaziado cada vez que o sistema é iniciado.

### /usr

(*Unix system ressource*)/(Recurso do sistema Unix)  \
Pasta contendo os executáveis ​​do sistema que não são vitais para sua inicialização e seu funcionamento mínimo.  \
Sua arquitetura é semelhante à de /

### /var

Pasta com conteúdos de dados variáveis ​​do sistema, indicando seu status. Dividido em subpastas.

##### /var/lock

Conteúdo variável ​​de bloqueio.  \
Permite saber o estado de uso do programa ou [daemon](https://pt.wikipedia.org/wiki/Daemon_(computa%C3%A7%C3%A3o)) que não deve ser executado duas vezes ao mesmo tempo (gparted, updates, etc.).


##### /var/log

Diretório onde costumam ficar salvos [Arquivos de log](https://debian-handbook.info/browse/pt-BR/stable/sect.syslog.html) com [log de dados](https://pt.wikipedia.org/wiki/Log_de_dados).


##### /var/mail

Caixas de correio do usuário.

##### /var/run

Dados variáveis ​​temporários de programas em execução. É um link simbólico para o diretório `/run`. Exemplo de conteúdo deste diretório em uma estação com [Ubuntu Desktop](https://ubuntu.com/download/desktop) 20.04.1 LTS (Saída do comando: `ls -F /var/run/`): 

```
acpid.pid         initramfs/          snapd/
acpid.socket=     irqbalance/         snapd-snap.socket=
alsa/             lock/               snapd.socket=
avahi-daemon/     log/                speech-dispatcher/
blkid/            lvm/                spice-vdagentd/
console-setup/    lxc/                sudo/
crond.pid         mlocate.daily.lock  systemd/
crond.reboot      motd.d/             thermald/
cups/             mount/              tmpfiles.d/
dbus/             netns/              udev/
dmeventd-client|  NetworkManager/     udisks2/
dmeventd-server|  openvpn/            unattended-upgrades.lock
docker/           openvpn-client/     user/
docker.sock=      openvpn-server/     utmp
gdm3/             plymouth/           uuidd/
gdm3.pid          sendsigs.omit.d/    wpa_supplicant/
initctl|          shm@                xtables.lock
```

##### /var/spool

Fila para serviços, especialmente para impressoras, mensagens de e-mail ou tarefas agendadas.


##### /var/tmp

Arquivos temporários, eles não são excluídos a cada início.


##### /var/www

Diretório padrão dos servidores web [Apache](http://httpd.apache.org/) ou [Nginx](http://nginx.org/).


## Particionamento

É aconselhável particionar seu sistema, ou seja, criar diferentes partições para separar as partes "independentes". Assim, em caso de reinstalação do sistema, algumas peças personalizadas já estarão no local sem a necessidade de restaurá-las.


#### /home

Provavelmente o diretório mais importante para separar! Portanto, em caso de destruição de seu sistema ou reinstalação, seus dados pessoais e configurações permanecerão no local. É aconselhável tornar essa partição o maior possível.

#### /opt

Também é muito importante no caso de você instalar muitos softwares manualmente (por exemplo, jogos).
Eu pessoalmente recomendo um tamanho base de 20 GiB, para se adaptar de acordo com suas necessidades.


#### /boot

Permite separar os arquivos de inicialização.
Um tamanho de 300 MiB será mais do que suficiente.

#### /tmp

Permite separar os arquivos temporários que serão apagados a cada inicialização do sistema. Uma partição separada só deve ser criada de acordo com a aplicação que será feita do servidor.


#### /

Por implicação "o resto dos diretórios", um tamanho de 10 GiB a 20 GiB será suficiente.

## Veja também 

- [Em Inglês -- site web do FHS](http://www.pathname.com/fhs/)    
- {ref}`arvore-de-diretorios`
