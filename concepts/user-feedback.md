# 💬 Feedback ao Usuário (User Feedback)

## 💡 O que é

**Feedback ao usuário** é qualquer resposta visual, sonora ou tátil que um sistema fornece para comunicar o resultado de uma ação. Em interfaces digitais, o feedback é um princípio central de usabilidade: o usuário precisa saber se sua ação foi bem-sucedida, se ocorreu um erro ou se o sistema ainda está processando algo.

Sem feedback, o app parece "quebrado" — o usuário não sabe se clicou no botão, se o dado foi salvo ou se precisa tentar novamente. Um bom feedback é imediato, claro e proporcional à importância da ação.

Os tipos mais comuns em apps mobile são: **Toast/Snackbar** (mensagem temporária na parte inferior), **AlertDialog** (caixa de diálogo modal), **ChooseDialog** (diálogo com opções de escolha) e mudanças visuais de estado nos componentes.

## ⚙️ Como é usado neste projeto

O app implementa feedback em todos os pontos críticos do fluxo:

| Situação                        | Tipo de feedback       | Mensagem                              |
| ------------------------------- | ---------------------- | ------------------------------------- |
| Título vazio ao cadastrar       | Alert (Notifier)       | "Insira um título para continuar!"    |
| Gênero não selecionado          | Alert (Notifier)       | "Selecione um gênero para continuar!" |
| Livro cadastrado com sucesso    | Alert (Notifier)       | "Livro cadastrado com sucesso!"       |
| Livro atualizado com sucesso    | Alert (Notifier)       | "Livro atualizado com sucesso!"       |
| Livro excluído com sucesso      | Alert (Notifier)       | "Livro excluído com sucesso!"         |
| Clique em livro da lista        | Choose Dialog (Opções) | EDITAR / EXCLUIR / CANCEL             |
| Confirmação antes de excluir    | Choose Dialog          | SIM, EXCLUIR / CANCELAR               |

## 🔍 Exemplo do projeto

```
// Feedback de erro — campo inválido
call Avisos.Show Alert
  notice → "Insira um título para continuar!"

// Feedback de sucesso — após cadastro
call Avisos.Show Alert
  notice → "Livro cadastrado com sucesso!"

// Feedback de confirmação — antes de excluir
call Confirmacao_exclusao.Show Choose Dialog
  message → "Tem certeza que deseja excluir o livro?"
  title   → "Confirmação de Exclusão"
  button1 → "SIM, EXCLUIR"
  button2 → "CANCELAR"
```

## 📚 Recursos para aprofundamento

- [10 Heurísticas de Nielsen — #1: Visibilidade do status do sistema](https://www.nngroup.com/articles/ten-usability-heuristics/) — princípio de usabilidade que fundamenta o feedback
- [Snackbars — Material Design](https://m3.material.io/components/snackbar/overview) — guia de uso de mensagens temporárias em Android
