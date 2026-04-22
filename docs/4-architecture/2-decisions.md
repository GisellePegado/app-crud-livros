# ⚖️ Decisões de Arquitetura (ADRs)

## 🏛️ ADR-001 — Kodular como plataforma de desenvolvimento

**📅 Data:** 2025  
**🚦 Status:** ✅ Aceita

### 💡 Contexto
O projeto é uma prática acadêmica da disciplina Fundamentos de Design de Sistemas, com foco em aplicar conceitos de design e banco de dados. O tempo disponível para desenvolvimento é limitado e o objetivo é a experimentação prática, não a entrega de um produto de produção.

### 🚀 Decisão
Utilizar o **Kodular**, plataforma low-code baseada em blocos visuais, para criar o app Android sem escrever código nativo.

### 📈 Consequências

**✅ Vantagens:**
- Curva de aprendizado muito baixa — permite focar no design e na lógica sem se preocupar com sintaxe
- Geração de APK nativa para Android sem necessidade de SDK ou ambiente de desenvolvimento complexo
- Integração nativa com Firebase Realtime Database disponível como componente visual

**⚠️ Desvantagens/Riscos:**
- Lógica do app fica presa na plataforma Kodular — não há código-fonte exportável em linguagem convencional
- Recursos avançados (animações complexas, customização profunda de UI) são limitados
- Escalabilidade reduzida para projetos maiores

---

## 🏛️ ADR-002 — Firebase Realtime Database como banco de dados

**📅 Data:** 2025  
**🚦 Status:** ✅ Aceita

### 💡 Contexto
O app precisa persistir dados (livros e gêneros) e sincronizá-los entre sessões. As alternativas consideradas foram armazenamento local (TinyDB do Kodular) e banco de dados em nuvem.

### 🚀 Decisão
Utilizar o **Firebase Realtime Database** para armazenar e sincronizar os dados do catálogo.

### 📈 Consequências

**✅ Vantagens:**
- Dados persistidos na nuvem e acessíveis de qualquer dispositivo
- Sincronização em tempo real sem necessidade de polling
- Integração nativa no Kodular via componente Firebase DB
- Gêneros podem ser gerenciados diretamente no painel do Firebase sem alterar o app

**⚠️ Desvantagens/Riscos:**
- Requer conexão com a internet — o app não funciona offline
- O título do livro é usado como chave (tag), o que impede dois livros com o mesmo título
- Estrutura NoSQL (JSON) não oferece integridade referencial entre livros e gêneros

---

## 🏛️ ADR-003 — Título do livro como chave primária no Firebase

**📅 Data:** 2025  
**🚦 Status:** ✅ Aceita

### 💡 Contexto
O Firebase Realtime Database organiza dados como pares chave-valor. O Kodular expõe essa estrutura via `Store Value (tag, value)`. Era necessário definir o que seria usado como chave única dos livros.

### 🚀 Decisão
Utilizar o **título do livro** como tag (chave) no nó `bdCadastrar`, armazenando o gênero como valor.

### 📈 Consequências

**✅ Vantagens:**
- Simplicidade de implementação — sem necessidade de geração de IDs únicos
- Facilita a operação de edição e exclusão, que já conhece o título ao selecionar da lista

**⚠️ Desvantagens/Riscos:**
- Dois livros com o mesmo título se sobrescrevem — não há suporte a títulos duplicados
- Uma solução mais robusta usaria IDs únicos gerados automaticamente (timestamp ou UUID)
