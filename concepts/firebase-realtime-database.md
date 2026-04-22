# ☁️ Banco de Dados em Tempo Real (Firebase Realtime Database)

## 💡 O que é

O **Firebase Realtime Database** é um banco de dados NoSQL hospedado na nuvem pela Google que armazena e sincroniza dados entre clientes em tempo real. Ao contrário de bancos de dados relacionais (que usam tabelas e SQL), o Firebase organiza todos os dados em uma única árvore JSON — uma estrutura de chave-valor aninhada.

O diferencial mais importante é a sincronização automática: quando um dado é alterado no banco, todos os clientes conectados recebem a atualização instantaneamente, sem necessidade de polling ou requisições manuais. Isso o torna ideal para apps mobile que precisam de dados sempre atualizados.

## ⚙️ Como é usado neste projeto

O app usa dois nós distintos no banco para separar as responsabilidades:

| Nó no Firebase | Componente Kodular | Função                              |
| -------------- | ------------------ | ----------------------------------- |
| `bdCadastrar/` | `bdCadastrar`      | Armazena e remove livros            |
| `bdGeneros/`   | `bdGeneros`        | Fornece a lista de gêneros ao Spinner |
| `bdCadastrar/` | `bdListar`         | Lê a lista de livros para exibição  |

A separação entre `bdCadastrar` e `bdListar` — mesmo apontando para o mesmo nó — permite que a lógica de escrita e leitura seja controlada de forma independente nos blocos.

## 🔍 Exemplo do projeto

```json
// Estrutura real dos dados no Firebase

{
  "bdCadastrar": {
    "O Iluminado": "Terror",
    "Duna": "Ficção",
    "Harry Potter e a Pedra Filosofal": "Fantasia"
  },
  "bdGeneros": {
    "Terror": "Terror",
    "Ficção": "Ficção",
    "Fantasia": "Fantasia",
    "Romance": "Romance",
    "Suspense": "Suspense"
  }
}
```

```
// Bloco de inicialização — carrega gêneros ao abrir o app
when Screen1.Initialize
  call bdGeneros.Get Tag List
```

## 📚 Recursos para aprofundamento

- [Firebase Realtime Database](https://firebase.google.com/docs/database) — documentação oficial
- [Estrutura do banco de dados](https://firebase.google.com/docs/database/android/structure-data) — boas práticas de modelagem JSON
