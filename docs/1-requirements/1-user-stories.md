# 📖 Histórias de Usuário

> Prática da disciplina **Fundamentos de Design de Sistemas** — UNINTER  
> App desenvolvido com Kodular + Firebase Realtime Database

---

## 📑 HU-01 — Cadastrar um livro

**Como** usuário do aplicativo,  
**quero** informar o título e o gênero de um livro e salvá-lo,  
**para que** eu possa manter um catálogo pessoal de livros.

### ✅ Critérios de Aceitação

- [ ] O campo de título não pode estar vazio ao cadastrar
- [ ] O gênero deve ser selecionado (não pode permanecer em "Selecione...")
- [ ] Após o cadastro, o livro aparece na lista imediatamente
- [ ] Uma mensagem de sucesso é exibida ao concluir o cadastro

---

## 📑 HU-02 — Listar os livros cadastrados

**Como** usuário do aplicativo,  
**quero** visualizar todos os livros salvos no catálogo,  
**para que** eu possa consultar minha coleção a qualquer momento.

### ✅ Critérios de Aceitação

- [ ] A lista exibe título e gênero de cada livro
- [ ] A lista pode ser exibida ou ocultada por um botão
- [ ] Os dados são carregados diretamente do Firebase

---

## 📑 HU-03 — Editar um livro cadastrado

**Como** usuário do aplicativo,  
**quero** selecionar um livro da lista e alterar seu título ou gênero,  
**para que** eu possa corrigir informações incorretas.

### ✅ Critérios de Aceitação

- [ ] Ao selecionar um livro, os campos são preenchidos automaticamente com os dados atuais
- [ ] O título e o gênero atual do livro são carregados corretamente nos campos de edição
- [ ] O botão muda para "ATUALIZAR" ao entrar em modo de edição
- [ ] Campos vazios ou gênero não selecionado impedem a atualização
- [ ] Uma mensagem de sucesso é exibida após atualizar

---

## 📑 HU-04 — Excluir um livro cadastrado

**Como** usuário do aplicativo,  
**quero** remover um livro do catálogo,  
**para que** eu possa manter a lista organizada sem títulos indesejados.

### ✅ Critérios de Aceitação

- [ ] Uma confirmação é solicitada antes de excluir
- [ ] O livro é removido da lista imediatamente após confirmação
- [ ] Uma mensagem de sucesso é exibida após a exclusão
- [ ] Cancelar a confirmação não remove o livro

---

## 📑 HU-05 — Selecionar gênero a partir de lista dinâmica

**Como** usuário do aplicativo,  
**quero** escolher o gênero do livro a partir de uma lista atualizada,  
**para que** eu use sempre os gêneros disponíveis no sistema, sem digitar manualmente.

### ✅ Critérios de Aceitação

- [ ] A lista de gêneros é carregada automaticamente do Firebase ao abrir o app
- [ ] O campo de gênero exibe "Selecione..." por padrão
- [ ] Não é possível cadastrar ou editar sem escolher um gênero válido

---

## 🌐 Contexto

O aplicativo **Catálogo de Livros** foi desenvolvido como prática da disciplina Fundamentos de Design de Sistemas. Em aula foram construídas as funcionalidades de cadastro e listagem com conexão ao Firebase. As funcionalidades de edição e exclusão foram implementadas de forma independente, completando o ciclo CRUD do app.
