(wireshark-grupo)=

# Wireshark

> Membros do grupo *wirehark* serão capazes de capturar pacotes nas interfaces de rede. Esta é a forma preferida de instalação se o Wireshark/Tshark forem usados para capturar e exibir pacotes ao mesmo tempo, uma vez que dessa forma, apenas o processo *dumpcap* deve ser executado com privilégios elevados graças à [separação de privilégios][^1].
> Observe que nenhum usuário será adicionado ao grupo wirehark automaticamente; um administrador do sistema deve adicioná-los manualmente, usando o comando `usermod`:
> 
> - `sudo usermod -a -G wirehark $USER`
> 
> ou, se você estiver usando um ambiente de trabalho que inclui uma ferramenta gráfica para gerenciamento de usuários, como a ferramenta "Usuários e grupos" no GNOME (encontrado no pacote *gnome-system-tools*), usando essa ferramenta. Depois de um usuário é adicionado ao grupo WireShark, ele/ela pode precisar fazer login novamente para fazer com que sua nova associação ao grupo entre em vigor e seja capaz de capturar pacotes.
>
> [Installing dumpcap and allowing non-root users to capture packets](https://code.wireshark.org/review/gitweb?p=wireshark.git;a=blob_plain;f=debian/README.Debian)


Para listar usuários que pertencem ao grupo *wireshark*, execute o comando:

- `getent group wireshark`


[^1]: <https://wiki.wireshark.org/Development/PrivilegeSeparation>