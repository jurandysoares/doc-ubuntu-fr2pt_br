(ocultos)=

# Pastas e arquivos ocultos

- Traduzido de: <http://doc.ubuntu-fr.org/fichier_cache>
- Tradutor: Jurandy Soares
- Data da tradução: 04/jan/2021

## Definição e utilidade

Itens ocultos são itens que não são visíveis por padrão quando o usuário visualiza o conteúdo de uma pasta. Esta possibilidade de ocultar elementos permite proteger os arquivos de manipulações não intencionais e tornar mais leve a visualização das pastas nas quais estão armazenados.
Os elementos ocultos podem ser reconhecidos pelo ponto antes de seus nomes. Um arquivo denominado "**.teste**" será, portanto, reconhecido pelo sistema como um arquivo oculto, enquanto um arquivo denominado "**teste**" não será.

## Exibir itens escondidos


```{warning}
Existem muitas situações em que pode ser útil exibir esses itens. Observe, no entanto, que se esses arquivos estiverem ocultos, é por um bom motivo ... portanto, tome cuidado com seu manuseio.
```

### Atalho de teclado

Esses atalhos de teclado são válidos na maioria dos aplicativos.

- No Ubuntu e no Xubuntu: {kbd}`Ctrl+h` ("h" para "escondido" = oculto em inglês)
- No Kubuntu: {kbd}`Alt+.`

### No gerenciador de arquivos

A maioria dos gerenciadores de arquivos tem uma caixa de seleção localizada no menu "Exibir". Esta caixa é freqüentemente chamada de "Exibir arquivos ocultos". Por exemplo, em Thunar , abra o menu Exibir e marque a caixa "Exibir arquivos ocultos".

Em outros aplicativos gráficos
No menu “Abrir…” ou “Salvar como…” de alguns aplicativos, os dois métodos anteriores não funcionam, mas pode ser útil salvar um arquivo em uma pasta oculta. Normalmente, é suficiente clicar com o botão direito no gerenciador de arquivos e selecionar "Exibir arquivos ocultos".

### Através de um terminal

Para listar em um terminal os elementos não ocultos da pasta atual, digite o comando:
- `ls`

Para exibir todos os itens, incluindo itens ocultos, basta adicionar o argumento `-a` ("todos" em Inglês):
- `ls -a`

E para mostrar apenas arquivos e pastas ocultos:
- `ls -d .*`

Se você adicionar `/`, verá apenas as pastas ocultas:
- `ls -d .*/`
  
Clique em [ls](http://manpages.ubuntu.com/ls) para obter mais informações sobre como usar o comando `ls`.

## Dicas

### Arquivo `.hidden` (oculto em Inglês)

Se você deseja tornar um elemento invisível no Nautilus, em cada pasta em questão, crie um arquivo de texto com o nome `.hidden` e coloque o nome dos elementos que deseja ocultar nele. Deve haver apenas um item por linha.
(Este truque apenas torna os arquivos invisíveis no Nautilus, eles permanecerão visíveis no modo de console.)

Por exemplo, para aplicar este truque a um conjunto de arquivos com a extensão `*.pyc`, você pode usar os seguintes comandos:

- `ls -1 * .pyc> .hidden`

  se você deseja SUBSTITUIR a lista de arquivos ocultos. anteriormente

- `ls -1 *.pyc >> .hidden` 

  se você deseja ADICIONAR novos arquivos ocultos.


