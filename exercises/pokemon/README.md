# Cadastro de Pokémons

Neste exercício, criaremos dois pequenos scripts: `cadastrar.sh` e `visualizar.sh`.
O objetivo é permitir gravar em um arquivo de texto os dados sobre um determinado
Pokémon e depois ser capaz de listar esses dados.

## Fluxo

### `cadastrar.sh`

- Deve perguntar os seguintes dados: **nome** e **tipo**
- Deve gravar em formato `nome tipo`, uma linha para cada Pokémon
- Deve criar um arquivo `pokemon.txt` se não existir e, se existir, concatenar o conteúdo ao final do arquivo

### Dica:

- Use `read` para ler os dados

### `visualizar.sh`

- Deve abrir o `pokemon.txt` e imprimir seu conteúdo na tela. Você pode brincar de tentar formatar a saída!

#### Dica:

- Você pode usar o comando `cat`
- Se quiser, pode usar `grep` para consultar os dados de algum Pokémon específico
