# 📱 Componentes de Interface Mobile (Mobile UI Components)

## 💡 O que é

**Componentes de interface mobile** são elementos visuais reutilizáveis que formam a tela de um aplicativo — botões, campos de texto, listas, menus suspensos e diálogos. Cada componente tem um comportamento padrão definido pelo sistema operacional (Android ou iOS) e pode ser configurado e estendido pelo desenvolvedor.

Escolher os componentes certos para cada interação é uma decisão de design que impacta diretamente a usabilidade do app. Um Spinner, por exemplo, é ideal para listas curtas de opções fixas; um campo de texto livre é melhor para entradas abertas. Diálogos de confirmação existem para proteger o usuário de ações irreversíveis.

## ⚙️ Como é usado neste projeto

O app **Catálogo de Livros** utiliza os seguintes componentes de interface do Kodular:

| Componente       | Tipo              | Função no app                                              |
| ---------------- | ----------------- | ---------------------------------------------------------- |
| `txtTitulo`      | TextBox           | Campo de entrada livre para o título do livro              |
| `spnGenero`      | Spinner           | Menu suspenso com a lista de gêneros carregada do Firebase |
| `btnCadastrar`   | Button            | Botão que alterna entre CADASTRAR e ATUALIZAR              |
| `btnListar`      | Button            | Botão que alterna entre EXIBIR LISTA e OCULTAR LISTA       |
| `listaLivros`    | ListView          | Lista rolável que exibe título e gênero de cada livro      |
| `Opcoes`         | Choose Dialog     | Diálogo com opções EDITAR e EXCLUIR ao clicar num livro    |
| `Confirmacao_exclusao` | Choose Dialog | Diálogo de confirmação antes de excluir um livro      |
| `Avisos`         | Notifier          | Exibe Snackbar/Toast com mensagens de sucesso e erro       |

## 🔍 Exemplo do projeto

```
// Spinner com placeholder e lista dinâmica
when bdGeneros.Tag List
  set spnGenero.Elements to get value
  insert list item list spnGenero.Elements index 1 item "Selecione..."
  set spnGenero.Elements to spnGenero.Elements   // força re-render
  set spnGenero.Selection to "Selecione..."

// ListView exibindo título (title) e gênero (subtitle)
when bdListar.Got Value
  call listaLivros.Add Item
    title    → get tag
    subtitle → join "Gênero:" get value
```

![Lista de gêneros no Spinner](../assets/generos.gif)

## 📚 Recursos para aprofundamento

- [Kodular — Componentes de UI](https://docs.kodular.io/components/user-interface/) — referência de todos os componentes de interface
- [Material Design — Android](https://m3.material.io/components) — guia de design dos componentes nativos Android
