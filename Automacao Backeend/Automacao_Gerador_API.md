# 📜🤪 Automação | Gerador de API – APIDAMASSA Generator

“Um gerador automático de APIs rápidas, completas e configuráveis — feito pra dev que gosta de praticidade e não tem tempo a perder.”

## 🏷 Nome do projeto:

### `🎉 APIDAMASSA Generator`

🤖 O que ele faz?

### O APIDAMASSA Generator cria automaticamente uma estrutura funcional completa de API Node.js com Express — ideal para estudos, testes, experimentos e simulações.

## A ideia é simples:

👉 Você executa o script
👉 Ele monta toda a API com pastas, arquivos e lógica inicial
👉 Você só faz requisições e começa a brincar

Perfeito para aprender:

Como uma API nasce

Como organizar pastas

Como rotas, controllers e services conversam

Como funciona o backend no mundo real

## 📁 api/

Estrutura principal da sua API.

## 📁 api/routes

Onde ficam as rotas (GET, POST, PUT, DELETE).

## 📁 api/controllers

Processamento das rotas.

## 📁 api/services

Regras de negócio simples + funções reaproveitáveis.

## 📁 api/models

Simulação de dados / estrutura de “model”.

## 📁 docs

Documentação automática da API.

## 📁 tests

Futuras brincadeiras com testes.

## 📁 logs

Histórico básico de execuções e requisições.

## 🏁 Como usar
1️⃣ Crie uma pasta vazia

Será a pasta onde sua API será gerada.

## 2️⃣ Crie um arquivo de texto

Exemplo:

apida.sh

## 3️⃣ Cole o script completo dentro dele
## 4️⃣ Salve o arquivo com extensão .sh

Exemplo:

apida.sh

## 5️⃣ Dê permissão para execução (Linux/macOS)
chmod +x apida.sh

## 6️⃣ Execute:
./apida.sh

## 7️⃣ Após gerar, instale as dependências:
npm install

## 8️⃣ Inicie a API:
npm start

```bash
#!/bin/bash

echo "============================================"
echo "      🚀 APIDAMASSA Generator v1.0"
echo "============================================"
sleep 1

echo "📁 Criando estrutura de pastas..."

mkdir -p api/routes
mkdir -p api/controllers
mkdir -p api/services
mkdir -p api/models
mkdir -p docs
mkdir -p tests
mkdir -p logs

echo "📄 Criando arquivos base..."

# ---------------------------
# app.js
# ---------------------------
cat << 'EOF' > app.js
const express = require('express');
const app = express();
const path = require('path');

// Middlewares
app.use(express.json());
app.use(express.urlencoded({ extended: true }));

// Rotas
const userRoutes = require('./api/routes/userRoutes');
app.use('/users', userRoutes);

// Rota principal
app.get('/', (req, res) => {
  res.json({
    message: "🔥 APIDAMASSA está ON!",
    docs: "/docs",
    example: "/users"
  });
});

module.exports = app;
EOF

# ---------------------------
# server.js
# ---------------------------
cat << 'EOF' > server.js
const app = require('./app');
require('dotenv').config();

const PORT = process.env.PORT || 3000;

app.listen(PORT, () => {
  console.log("🚀 APIDAMASSA rodando na porta " + PORT);
});
EOF

# ---------------------------
# userRoutes.js
# ---------------------------
cat << 'EOF' > api/routes/userRoutes.js
const express = require('express');
const router = express.Router();
const controller = require('../controllers/userController');

router.get('/', controller.getUsers);
router.post('/', controller.createUser);

module.exports = router;
EOF

# ---------------------------
# userController.js
# ---------------------------
cat << 'EOF' > api/controllers/userController.js
const service = require('../services/userService');

exports.getUsers = (req, res) => {
  res.json(service.listUsers());
};

exports.createUser = (req, res) => {
  const user = service.addUser(req.body);
  res.json(user);
};
EOF

# ---------------------------
# userService.js
# ---------------------------
cat << 'EOF' > api/services/userService.js
let users = [
  { id: 1, nome: "Fulano" },
  { id: 2, nome: "Ciclano" }
];

exports.listUsers = () => users;

exports.addUser = (data) => {
  const novo = {
    id: users.length + 1,
    nome: data.nome || "Usuário sem nome"
  };
  users.push(novo);
  return novo;
};
EOF

# ---------------------------
# Model (simples)
# ---------------------------
cat << 'EOF' > api/models/userModel.js
// Modelo simples (mockado)
module.exports = {
  id: Number,
  nome: String
};
EOF

# ---------------------------
# .env
# ---------------------------
cat << 'EOF' > .env
PORT=3000
EOF

# ---------------------------
# package.json
# ---------------------------
cat << 'EOF' > package.json
{
  "name": "apida-massa",
  "version": "1.0.0",
  "description": "Gerador automático de API para estudos",
  "main": "server.js",
  "scripts": {
    "start": "node server.js",
    "dev": "nodemon server.js"
  },
  "dependencies": {
    "express": "^4.19.2",
    "dotenv": "^16.4.5"
  }
}
EOF

# ---------------------------
# docs/readme.md
# ---------------------------
cat << 'EOF' > docs/readme.md
# 📚 Documentação da APIDAMASSA

API criada automaticamente para estudos.

## Rotas disponíveis:
- GET /users
- POST /users

Projeto gerado com ❤️ pelo APIDAMASSA Generator.
EOF

# ---------------------------
# .gitignore
# ---------------------------
cat << 'EOF' > .gitignore
node_modules/
.env
logs/
EOF

echo "============================================"
echo "🔥 APIDAMASSA criada com sucesso!"
echo "👉 Para iniciar: npm install && npm start"
echo "============================================"

````




