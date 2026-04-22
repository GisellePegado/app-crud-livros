# 🔁 CRUD (Create, Read, Update, Delete)

## 💡 O que é

CRUD é um acrônimo que representa as quatro operações fundamentais de qualquer sistema que persiste dados: **Create** (criar), **Read** (ler), **Update** (atualizar) e **Delete** (excluir). Essas operações formam a base de praticamente todos os sistemas de gerenciamento de informações, desde aplicativos simples até sistemas corporativos complexos.

O conceito vai além de uma lista de funções — ele define o ciclo de vida completo de um dado dentro do sistema. Um dado só é verdadeiramente gerenciável quando todas as quatro operações estão disponíveis ao usuário.

## ⚙️ Como é usado neste projeto

O app **Catálogo de Livros** implementa o CRUD completo sobre a entidade **Livro**, com os dados persistidos no Firebase Realtime Database:

| Operação | Ação no app                          | Componente Firebase      |
| -------- | ------------------------------------ | ------------------------ |
| Create   | Cadastrar novo livro                 | `bdCadastrar.Store Value`|
| Read     | Listar livros cadastrados            | `bdListar.Get Tag List`  |
| Update   | Editar título ou gênero de um livro  | `bdCadastrar.Store Value`|
| Delete   | Excluir livro após confirmação       | `bdCadastrar.Clear Tag`  |

> [!NOTE]
> O Create e o Update usam o mesmo componente (`Store Value`) porque o Firebase sobrescreve o valor quando a tag (título) já existe — o que naturalmente implementa a atualização.

## 🔍 Exemplo do projeto

```
-- CRIAR
when btnCadastrar.Click → btnCadastrar.Text = "CADASTRAR"
  call bdCadastrar.Store Value
    tag   → txtTitulo.Text
    value → spnGenero.Selection

-- ATUALIZAR (mesma operação, tag existente)
when btnCadastrar.Click → btnCadastrar.Text = "ATUALIZAR"
  call bdCadastrar.Store Value
    tag   → global livroSelecionado
    value → spnGenero.Selection

-- EXCLUIR
when Confirmacao_exclusao.After Choosing → choice = "SIM, EXCLUIR"
  call bdCadastrar.Clear Tag
    tag → global livroSelecionado
```

## 📚 Recursos para aprofundamento

- [CRUD — MDN Web Docs](https://developer.mozilla.org/pt-BR/docs/Glossary/CRUD) — definição e contexto web
- [Firebase Realtime Database - Ler e Gravar Dados](https://firebase.google.com/docs/database/android/read-and-write) — documentação oficial das operações no Firebase
