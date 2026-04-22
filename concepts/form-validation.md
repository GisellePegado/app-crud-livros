# ✅ Validação de Formulário (Form Validation)

## 💡 O que é

**Validação de formulário** é o processo de verificar se os dados inseridos pelo usuário atendem aos requisitos necessários antes de serem processados ou enviados. Ela protege o sistema de dados inconsistentes, incompletos ou inválidos — e orienta o usuário a corrigir erros antes de prosseguir.

A validação pode acontecer no cliente (antes de enviar) ou no servidor (após receber os dados). Em apps mobile, a validação no cliente é preferida porque oferece feedback imediato sem depender de uma requisição à rede.

Existem dois tipos principais: **validação de presença** (o campo foi preenchido?) e **validação de formato** (o valor está no formato correto?). Este projeto implementa os dois de forma combinada.

## ⚙️ Como é usado neste projeto

O app valida dois campos antes de permitir o cadastro ou a edição de um livro:

1. **Título** — verificação de presença: o campo não pode estar vazio
2. **Gênero** — verificação de seleção: o Spinner não pode estar em "Selecione..."

Ambas as validações são executadas no evento `when btnCadastrar.Click`, usando a técnica de **Guard Clause** — checar os erros primeiro e interromper o fluxo antes de chegar na operação principal.

## 🔍 Exemplo do projeto

```
when btnCadastrar.Click

  // Guard Clause 1 — título vazio
  if is empty txtTitulo.Text
    then call Avisos.Show Alert "Insira um título para continuar!"

  // Guard Clause 2 — gênero não selecionado
  else if spnGenero.Selection = "Selecione..."
    then call Avisos.Show Alert "Selecione um gênero para continuar!"

  // Só chega aqui se ambos os campos forem válidos
  else
    [lógica de cadastro ou atualização]
```

> [!TIP]
> A mesma lógica de validação se aplica ao modo de edição (botão ATUALIZAR), garantindo consistência dos dados em ambas as operações de escrita.

## 📚 Recursos para aprofundamento

- [Form Validation — MDN Web Docs](https://developer.mozilla.org/pt-BR/docs/Learn/Forms/Form_validation) — conceitos gerais de validação
- [Guard Clause — Refactoring Guru](https://refactoring.guru/replace-nested-conditional-with-guard-clauses) — padrão de simplificação de condicionais
