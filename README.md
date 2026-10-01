# 💰 FinançApp

> Controle financeiro pessoal diário com login, banco de dados por usuário e hospedagem gratuita.

🌐 **Acesse agora:** [financapp-c3641.web.app](https://financapp-c3641.web.app)

---

## 📸 Visão Geral

O FinançApp é uma aplicação web completa para controle de finanças pessoais. Roda 100% no navegador, sem backend próprio — toda a infraestrutura é Firebase (Auth + Firestore + Hosting).

Cada usuário possui seu próprio banco de dados isolado, acessível de qualquer dispositivo após o login.

---

## ✨ Funcionalidades

- 🔐 **Login seguro** — E-mail/senha ou conta Google
- 📊 **Dashboard** — Cards de saldo, saídas do mês, entradas e gasto diário
- ⚡ **Registro rápido** — Parser de texto livre no estilo WhatsApp/Notion
- 📋 **Entrada em lote** — Cole múltiplas linhas de uma vez
- 📈 **Gráficos** — Pizza por categoria e barras de evolução diária
- 🔍 **Histórico completo** — Tabela com filtros por busca, categoria e período
- ✏️ **Edição e exclusão** — Gerencie qualquer lançamento
- 📤 **Exportação XLSX** — Planilha Excel formatada por período
- 💾 **Backup/Restore JSON** — Exporta e importa todos os dados localmente
- 🌙 **Dark mode** — Tema escuro/claro com toggle
- 📱 **Responsivo** — Funciona em desktop e mobile

---

## 🛠️ Tecnologias

| Tecnologia | Uso |
|---|---|
| **Firebase Auth** | Autenticação (Email + Google OAuth) |
| **Cloud Firestore** | Banco de dados NoSQL por usuário em tempo real |
| **Firebase Hosting** | Hospedagem HTTPS gratuita |
| **Tailwind CSS** | Estilização responsiva com dark mode |
| **Chart.js** | Gráficos de pizza e barras |
| **SheetJS (XLSX)** | Exportação de planilha Excel |
| **Lucide Icons** | Ícones SVG |

---

## 📁 Estrutura do Projeto

```
financapp/
├── README.md
├── .gitignore
├── Dashboard de Controle Financeiro Diário_Responsivo.html  ← versão original (IndexedDB)
└── financapp-firebase/                                       ← versão com Firebase
    ├── firebase.json          ← configuração do Hosting
    ├── .firebaserc            ← ID do projeto Firebase
    ├── firestore.rules        ← regras de segurança por usuário
    └── public/
        ├── index.html         ← tela de login/registro
        └── app.html           ← dashboard principal
```

---

## 🔒 Segurança

Os dados de cada usuário são isolados no Firestore pela regra:

```js
match /users/{userId}/transactions/{transactionId} {
  allow read, write: if request.auth != null
                     && request.auth.uid == userId;
}
```

Nenhum usuário consegue ler ou escrever dados de outro.

---

## 🚀 Como fazer o deploy

### Pré-requisitos
- Conta Google
- Node.js instalado
- Projeto criado no [Firebase Console](https://console.firebase.google.com)

### Passos

**1. Clonar o repositório**
```bash
git clone https://github.com/PSactiva/financapp.git
cd financapp/financapp-firebase
```

**2. Configurar o Firebase**

Em `public/index.html` e `public/app.html`, substitua o bloco `firebaseConfig` pelas credenciais do seu projeto Firebase.

**3. Ativar os serviços no Firebase Console**
- Authentication → habilitar **E-mail/senha** e **Google**
- Firestore Database → criar banco → modo **Produção**
- Firestore → aba **Regras** → colar o conteúdo de `firestore.rules`

**4. Instalar a Firebase CLI e fazer o deploy**
```bash
sudo npm install -g firebase-tools
firebase login
firebase deploy --only hosting
```

---

## ⚡ Uso rápido

### Registro rápido por texto
Digite no campo de anotação e clique em **Preencher**:
```
25,50 Café Débito
120 Mercado Pix
45 Uber Transporte
3500 Salário recebido
```

### Entrada em lote
Na aba **Entrada em Lote**, cole várias linhas de uma vez (copiado do WhatsApp, Notion, bloco de notas).

### Exportar para Excel
Clique em **Exportar XLSX** → escolha o período → **Baixar Arquivo XLSX**.

---

## 📊 Plano Gratuito Firebase (Spark)

| Recurso | Limite | Status |
|---|---|---|
| Authentication | Ilimitado | ✅ |
| Firestore leituras/dia | 50.000 | ✅ |
| Firestore gravações/dia | 20.000 | ✅ |
| Armazenamento Firestore | 1 GB | ✅ |
| Hosting (banda/mês) | 360 MB | ✅ |

---

## 📝 Licença

MIT © [Paulo Activa](https://github.com/PSactiva)
