(chown-help)=

# chown --help

O texto abaixo é uma reformatação da saída do comando `chmod --help`

Uso: 

- `chown [OPÇÃO]... [DONO][:[GRUPO]] ARQUIVO...`
- `chown [OPÇÃO]... --reference=ARQREF ARQUIVO...`

Altera o dono e/ou grupo de cada ARQUIVO para DONO e/ou GRUPO.

Com `--reference`, altera o dono e grupo de cada ARQUIVO para o de ARQREF.

| Opção                           | Descrição                                                                                                                                                                                             |
| ------------------------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `-c`, `--changes`               | como verbose, mas só relata quando há uma alteração                                                                                                                                                   |
| `-f`, `--silent`, `--quiet`     | suprime a maioria das mensagens de erro                                                                                                                                                               |
| `-v`, `--verbose`               | emite um diagnóstico para cada arquivo processado                                                                                                                                                     |
| `--dereference`                 | afeta a referência de cada link simbólico em vez do próprio link em si (isso é o padrão)                                                                                                              |
| `-h`, `--no-dereference`        | afeta os links simbólicos em vez dos arquivos referenciados por elas (útil somente em sistemas que permitem mudar o dono de um link simbólico)                                                        |
| `--from=DONO_ATUAL:GRUPO_ATUAL` | muda dono e/ou grupo de cada arquivo apenas se seu dono e/ou grupo atual forem iguais aos especificados nesta opção. Um dos dois pode ser omitido, no caso de não ser exigido o teste de tal atributo |
| `--no-preserve-root`            | não trata "/" de forma diferenciada (o padrão)                                                                                                                                                        |
| `--preserve-root`               | falha ao operar recursivamente em "/"                                                                                                                                                                 |
| `--reference=ARQREF`            | usa o dono e o grupo do ARQREF ao invés de especificar os valores DONO:GRUPO                                                                                                                          |
| `-R`, `--recursive`             | opera em arquivos e diretórios recursivamente                                                                                                                                                         |

As seguintes opções modificam como uma hierarquia é percorrida quando a
opção `-R` é especificada também. Se mais de uma destas forem especificadas,
somente a última faz efeito.

- `-H`: se um argumento da linha de comando for um link simbólico para diretório, percorre-o
- `-L`: percorre toda link simbólico para diretório que for encontrada
- `-P`: não percorre links simbólicos (padrão)

Outras opções:

- `--help`: mostra esta ajuda e sai
- `--version`: informa a versão e sai

O dono, caso não seja informado, permanece inalterado. O grupo também não é
alterado se não informado, mas mudará para o grupo de login se deixado
implícito por ":" após um DONO simbólico.

DONO e GRUPO podem ser numéricos bem como simbólicos.

Exemplo:

  | Comando                | Descrição                                        |
  | ---------------------- | ------------------------------------------------ |
  | `chown root /u`        | Altera o dono de /u para "root".                 |
  | `chown root:equipe /u` | Idem, mas também altera seu grupo para "equipe". |
  | `chown -hR root /u`    | Altera o dono de /u e seus arquivos para "root". |

Página de ajuda do GNU coreutils: <https://www.gnu.org/software/coreutils/>  \
Relate erros de tradução do chown: <https://translationproject.org/team/pt_BR.html>  \
Documentação completa em: <https://www.gnu.org/software/coreutils/chown>  \
ou disponível localmente via: info "(coreutils) chown invocation"