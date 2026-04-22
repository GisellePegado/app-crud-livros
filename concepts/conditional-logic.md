# 🔀 Lógica Condicional (Conditional Logic)

## 💡 O que é

**Lógica condicional** é o mecanismo pelo qual um programa toma decisões: executa um bloco de código apenas quando determinada condição é verdadeira, e outro bloco quando é falsa. É a estrutura `if / else if / else` presente em praticamente todas as linguagens de programação e paradigmas.

Condicionais são essenciais para criar sistemas que reagem de forma diferente conforme o estado atual — sem elas, um app executaria sempre as mesmas ações independentemente do que o usuário fizesse ou do que os dados indicassem.

A qualidade das condicionais afeta diretamente a legibilidade e a manutenibilidade do código. Condicionais aninhadas demais (vários `if` dentro de `if`) tornam a lógica difícil de entender; técnicas como **Guard Clause** e separação de responsabilidades ajudam a manter a clareza.

## ⚙️ Como é usado neste projeto

O app usa lógica condicional em vários pontos críticos:

**Validação de campos** — três ramos `if / else if / else` que verificam título, gênero e modo (cadastrar vs. atualizar) antes de qualquer operação no Firebase.

**Controle de visibilidade da lista** — `if listaLivros.Visible` para alternar entre EXIBIR e OCULTAR LISTA e decidir se recarrega os dados.

**Controle do modo do botão** — `if btnCadastrar.Text = "CADASTRAR"` para diferenciar entre criar e atualizar.

**Resposta aos diálogos** — `if choice = "EDITAR"` e `if choice = "SIM, EXCLUIR"` para tratar as escolhas dos ChooseDialogs.

## 🔍 Exemplo do projeto

```
// Condicional de 3 ramos no botão Cadastrar/Atualizar

when btnCadastrar.Click

  if is empty txtTitulo.Text
    → exibe alerta de título vazio

  else if spnGenero.Selection = "Selecione..."
    → exibe alerta de gênero não selecionado

  else
    if btnCadastrar.Text = "CADASTRAR"
      → Store Value com o título digitado (novo registro)
    else
      → Store Value com livroSelecionado (atualização)

// Condicional no diálogo de opções
when Opcoes.After Choosing
  if choice = "EXCLUIR"
    → abre diálogo de confirmação
  else if choice = "EDITAR"
    → preenche campos e muda botão para ATUALIZAR
```

## 📚 Recursos para aprofundamento

- [Estruturas condicionais — Khan Academy](https://pt.khanacademy.org/computing/ap-computer-science-principles/programming-101/boolean-logic/a/conditionals-with-if-else) — introdução acessível ao conceito
- [Guard Clause — Refactoring Guru](https://refactoring.guru/replace-nested-conditional-with-guard-clauses) — técnica para simplificar condicionais aninhados
