# 🌐 Variáveis Globais (Global Variables)

## 💡 O que é

**Variáveis globais** são variáveis declaradas fora de qualquer função ou bloco específico, tornando-se acessíveis em qualquer parte do programa durante toda a sua execução. Elas armazenam um estado que precisa ser compartilhado entre diferentes eventos ou partes da lógica.

Em programação por blocos (como no Kodular), variáveis globais são especialmente importantes porque cada bloco de evento é independente — não há passagem de parâmetros direta entre eles. Variáveis globais funcionam como a "memória" do app: guardam o contexto de uma interação para que outro evento possa usar essa informação posteriormente.

O uso de variáveis globais deve ser criterioso: guardá-las demais torna o estado do app difícil de rastrear; guardá-las de menos obriga a repetir buscas desnecessárias.

## ⚙️ Como é usado neste projeto

O app utiliza três variáveis globais para manter o contexto do livro selecionado pelo usuário:

| Variável              | Tipo    | O que armazena                                          |
| --------------------- | ------- | ------------------------------------------------------- |
| `livroSelecionado`    | Texto   | Título do livro clicado na lista (usado como chave no Firebase) |
| `generoSelecionado`   | Texto   | Gênero do livro selecionado (já sem o prefixo "Gênero:") |
| `indiceSelecionado`   | Número  | Posição do livro na lista (índice da seleção)           |

Essas variáveis são preenchidas no evento `when listaLivros.Click` e consumidas nos eventos de edição e exclusão.

## 🔍 Exemplo do projeto

```
// Declaração das variáveis globais
initialize global indiceSelecionado to 0
initialize global livroSelecionado  to ""
initialize global generoSelecionado to ""

// Preenchimento ao clicar num livro
when listaLivros.Click
  set global indiceSelecionado  to get position
  set global livroSelecionado   to get title
  set global generoSelecionado  to replace all text
                                      get subtitle
                                      segment     "Gênero:"
                                      replacement ""

// Consumo no bloco de edição
when Opcoes.After Choosing → EDITAR
  set txtTitulo.Text      to get global livroSelecionado
  set spnGenero.Selection to get global generoSelecionado
```

## 📚 Recursos para aprofundamento

- [Variáveis no App Inventor](https://appinventor.mit.edu/explore/ai2/variables) — explicação de variáveis locais e globais em blocos
- [Global vs Local Variables — GeeksForGeeks](https://www.geeksforgeeks.org/global-and-local-variables-in-programming/) — comparação entre os dois tipos
