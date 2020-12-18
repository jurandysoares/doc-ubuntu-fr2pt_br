(virtualbox-grupo)=

# VirtualBox

> Os instaladores do Linux criam o grupo de usuários do sistema *vboxusers* durante a instalação. Qualquer usuário do sistema que usará dispositivos USB a partir da máquina virtual deverá ser membro desse grupo. Um usuário pode se tornar um membro do grupo *vboxusers* usando ferramentas gráficas de grupos e usuário ou com o seguinte comando:

> - `sudo usermod -aG vboxusers $USER`

> [2.3.4. The vboxusers Group](https://www.virtualbox.org/manual/ch02.html#install-linux-vboxusers)


Para listar usuários que pertencem ao grupo *vboxusers*, execute o comando:

- `getent group vboxusers`
