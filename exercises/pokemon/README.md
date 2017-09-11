# Cadastro de Pokémons

Neste exercício, criaremos dois pequenos scripts: `cadastrar.sh` e `consultar.sh`.
O objetivo é permitir gravar em um arquivo de texto os dados sobre um determinado
Pokémon e depois ser capaz de listar esses dados.

## Fluxo

### `cadastrar.sh`

- Deve perguntar os seguintes dados: **nome** e **tipo**
- Deve gravar em formato `nome tipo`, uma linha para cada Pokémon
- Deve criar um arquivo `pokemon.txt` se não existir e, se existir, concatenar o conteúdo ao final do arquivo

### Dica:

- Use `read` para ler os dados

### `consultar.sh`

- Deve ser chamado como `./consultar.sh Nome`
- Deve abrir o `pokemon.txt` e retornar a linha correspondente ao Pokémon

#### Dica:

- Você pode usar o comando `cat` para ler e `grep` para filtrar
