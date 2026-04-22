# 🛠️ Requisitos Funcionais

> Derivados das Histórias de Usuário HU-01 a HU-05.

Os requisitos funcionais descrevem **o que o sistema deve fazer**.

| ID   | Nome                          | Descrição                                                                 |
| ---- | ----------------------------- | ------------------------------------------------------------------------- |
| RF01 | Carregar gêneros do Firebase  | Ao iniciar o app, buscar a lista de gêneros cadastrados no Firebase       |
| RF02 | Exibir placeholder no Spinner | Inserir "Selecione..." como primeiro item da lista de gêneros             |
| RF03 | Validar título                | Impedir cadastro/edição se o campo de título estiver vazio                |
| RF04 | Validar gênero                | Impedir cadastro/edição se o gênero selecionado for "Selecione..."        |
| RF05 | Cadastrar livro               | Salvar título e gênero no Firebase Realtime Database                      |
| RF06 | Listar livros                 | Carregar e exibir todos os livros do Firebase em uma lista                |
| RF07 | Alternar visibilidade da lista| Exibir ou ocultar a lista de livros pelo botão EXIBIR/OCULTAR LISTA      |
| RF08 | Exibir opções do livro        | Ao clicar em um livro, mostrar diálogo com opções EDITAR e EXCLUIR        |
| RF09 | Editar livro                  | Preencher campos com dados do livro selecionado e permitir atualização    |
| RF10 | Confirmar exclusão            | Exibir diálogo de confirmação antes de excluir um livro                   |
| RF11 | Excluir livro                 | Remover o livro do Firebase após confirmação                              |
| RF12 | Exibir feedback das ações     | Mostrar mensagens de sucesso ou erro após cada operação                   |

---

## 🔗 Rastreabilidade: RF × Histórias de Usuário

| Requisito                    | HU-01 | HU-02 | HU-03 | HU-04 | HU-05 |
| ---------------------------- | :---: | :---: | :---: | :---: | :---: |
| RF01 — Carregar gêneros      |   —   |   —   |   —   |   —   |  ✅   |
| RF02 — Placeholder Spinner   |   —   |   —   |   —   |   —   |  ✅   |
| RF03 — Validar título        |  ✅   |   —   |  ✅   |   —   |   —   |
| RF04 — Validar gênero        |  ✅   |   —   |  ✅   |   —   |  ✅   |
| RF05 — Cadastrar livro       |  ✅   |   —   |   —   |   —   |   —   |
| RF06 — Listar livros         |   —   |  ✅   |   —   |   —   |   —   |
| RF07 — Alternar lista        |   —   |  ✅   |   —   |   —   |   —   |
| RF08 — Exibir opções         |   —   |   —   |  ✅   |  ✅   |   —   |
| RF09 — Editar livro          |   —   |   —   |  ✅   |   —   |   —   |
| RF10 — Confirmar exclusão    |   —   |   —   |   —   |  ✅   |   —   |
| RF11 — Excluir livro         |   —   |   —   |   —   |  ✅   |   —   |
| RF12 — Feedback das ações    |  ✅   |   —   |  ✅   |  ✅   |   —   |

---

## 💻 Implementação nos Blocos

| Requisito | Implementação no Kodular                                              |
| --------- | --------------------------------------------------------------------- |
| RF01      | `when Screen1.Initialize → call bdGeneros.Get Tag List`               |
| RF02      | `when bdGeneros.Tag List → insert list item index 1 "Selecione..."`   |
| RF03      | `when btnCadastrar.Click → if is empty txtTitulo.Text`                |
| RF04      | `when btnCadastrar.Click → else if spnGenero.Selection = "Selecione..."` |
| RF05      | `call bdCadastrar.Store Value tag txtTitulo value spnGenero.Selection` |
| RF06      | `when bdListar.Tag List → for each item → call bdListar.Get Value`    |
| RF07      | `when btnListar.Click → set listaLivros.Visible to not listaLivros.Visible` |
| RF08      | `when listaLivros.Click → call Opcoes.Show Choose Dialog`             |
| RF09      | `when Opcoes.After Choosing → choice = EDITAR → set campos + ATUALIZAR` |
| RF10      | `when Opcoes.After Choosing → choice = EXCLUIR → call Confirmacao_exclusao.Show Choose Dialog` |
| RF11      | `when Confirmacao_exclusao.After Choosing → choice = SIM, EXCLUIR → call bdCadastrar.Clear Tag` |
| RF12      | `call Avisos.Show Alert notice "Livro cadastrado/atualizado/excluído com sucesso!"` |
