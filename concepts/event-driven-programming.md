# ⚡ Programação Orientada a Eventos (Event-Driven Programming)

## 💡 O que é

**Programação orientada a eventos** é um paradigma no qual o fluxo de execução do programa é determinado por **eventos** — ações do usuário, sinais do sistema ou respostas de serviços externos. Em vez de o programa executar uma sequência linear de instruções do início ao fim, ele fica em espera e reage quando algo acontece.

Exemplos de eventos: um clique de botão, o carregamento de dados de uma API, a inicialização de uma tela, a escolha em um diálogo. Cada evento dispara um **handler** (bloco de tratamento) que contém a lógica a ser executada em resposta.

Esse paradigma é dominante no desenvolvimento de interfaces gráficas e apps mobile — é impossível prever quando o usuário vai tocar na tela, então o sistema precisa estar preparado para reagir a qualquer momento.

## ⚙️ Como é usado neste projeto

Toda a lógica do app **Catálogo de Livros** é estruturada em handlers de eventos. Não há um "main" ou sequência principal — cada bloco espera seu evento específico:

| Evento                              | Handler                          | O que faz                                    |
| ----------------------------------- | -------------------------------- | -------------------------------------------- |
| `Screen1.Initialize`                | Inicialização da tela            | Carrega os gêneros do Firebase               |
| `bdGeneros.Tag List`                | Resposta do Firebase (gêneros)   | Preenche o Spinner com a lista de gêneros    |
| `btnCadastrar.Click`                | Toque no botão                   | Valida campos e salva/atualiza no Firebase   |
| `btnListar.Click`                   | Toque no botão                   | Alterna visibilidade da lista                |
| `listaLivros.Click`                 | Toque num item da lista          | Abre diálogo de opções (editar/excluir)      |
| `Opcoes.After Choosing`             | Escolha no diálogo               | Direciona para edição ou exclusão            |
| `Confirmacao_exclusao.After Choosing`| Confirmação de exclusão         | Executa ou cancela a remoção do livro        |
| `bdListar.Tag List` + `Got Value`   | Resposta do Firebase (livros)    | Popula a ListView com os livros do banco     |

## 🔍 Exemplo do projeto

```
// Cadeia de eventos para listar livros:

// 1. Evento disparado pelo botão
when btnListar.Click
  set listaLivros.Visible to not listaLivros.Visible
  call AtualizarBotaoLista

// 2. AtualizarBotaoLista verifica estado e dispara busca no Firebase
to AtualizarBotaoLista
  if listaLivros.Visible
    call bdListar.Get Tag List
    set btnListar.Text to "OCULTAR LISTA"

// 3. Firebase responde com a lista de tags (títulos)
when bdListar.Tag List
  for each item in list
    call bdListar.Get Value tag item

// 4. Firebase responde com o valor de cada tag (gênero)
when bdListar.Got Value
  call listaLivros.Add Item title tag subtitle join "Gênero:" value
```

## 📚 Recursos para aprofundamento

- [Event-Driven Programming — Wikipedia](https://en.wikipedia.org/wiki/Event-driven_programming) — visão geral do paradigma
- [Kodular — Events](https://docs.kodular.io/blocks/control/) — referência de blocos de controle e eventos no Kodular
