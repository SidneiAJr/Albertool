# 🚀 Constellation Supreme CLI — Documentação Oficial
Foco: Angular + Backend (JS/TS/PHP)
Criado no Brasil 🇧🇷 para o mundo.

Bem-vindo à documentação técnica da Constellation Supreme CLI, uma ferramenta automatizada para criação rápida de estruturas profissionais de projetos Web utilizando Angular no frontend e JS, TS ou PHP no backend.

## 📌 Sobre a Ferramenta

A Constellation Supreme CLI é um script Shell focado em produtividade, permitindo criar projetos completos com organização profissional em segundos, sem instalações complexas.

- ✔ Simples — Apenas execute o script
- ✔ Modular — Escolha o tipo de backend
- ✔ Rápido — Estruturas prontas automaticamente
- ✔ Automático — Instala dependências e configura o Angular CLI

## 📦 Requisitos

Para executar corretamente:

- ✔ Git instalado
- ✔ Node.js instalado
- ✔ Angular CLI (será instalada automaticamente quando necessário)

## 📁 Estrutura Criada
A CLI cria automaticamente uma estrutura profissional contendo:
```bash
Backend/
 ├── app/
 │   ├── controller/
 │   ├── model/
 │   ├── service/
 │   ├── repository/
 │   ├── middleware/
 │   ├── entity/
 │   ├── dto/
 │   ├── config/
 │   ├── helpers/
 │   ├── utils/
 │   └── routes/
 ├── public/
 ├── tests/
 ├── scripts/
 ├── docs/
 ├── .env
 └── .gitignore
```

## 🟥 Frontend — Angular
```bash
Frontend_Angular/
 ├── src/
 │   ├── app/
 │   ├── assets/
 │   ├── environments/
 └── angular.json
 └── package.json
```

## 🟩 Dados de Teste
São criados dados auxiliares:
- ✔ JSON de Teste
- ✔ SQL de criação de banco

## 🙏 Agradecimento
- Obrigado a todos os desenvolvedores que utilizam a Constellation Supreme CLI.
- É simples, porém extremamente funcional e focada em produtividade.
- Se possível, aceitei um café ☕ como forma de apoio — agradeço demais!

## 📚 Como Usar
- Crie uma pasta no seu computador.
- Dentro dela, crie um arquivo de texto comum.
- Cole o script completo fornecido no GitHub.
- Salve com a extensão:
- setup.sh
- Clique com botão direito → Executar com Git Bash
- Escolha as opções no menu e deixe a CLI trabalhar sozinha.

## 🔧 Funcionalidades do Script
- ✔ Sistema de menu interativo
- ✔ Criação automática do backend (PHP / JS / TS)
- ✔ Criação automática do frontend (Angular)
- ✔ Instalação de dependências no backend
- ✔ Estrutura organizada para projetos profissionais
- ✔ Criação de arquivos base (controllers, services, models...)
- ✔ Criação de JSON e SQL de teste

## 📌 Tecnologias Suportadas
- A CLI é compatível com:
- Backend:
- JavaScript (Node.js / Express)
- TypeScript (Node.js / Express com TS)
- PHP
- Frontend:
- Angular (CLI Oficial)
- Nenhum outro frontend é criado nesta versão (React/Native removidos).

```bash
#!/bin/bash

echo "======================================"
echo "WELCOME!"
echo "SUPREME CONSTELLATIONS CLI"
echo "Pay one Coffee | Help For All Dev's"
echo "CLI MADE IN BRASIL"
echo "CLI for Dev's WEB"
echo "======================================"

read -p "Digite o nome do seu projeto: " PROJECT_NAME

# Diretórios base
BASE_DIR="$PROJECT_NAME"
BACKEND_DIR="$BASE_DIR/Backend"
FRONTEND_DIR="$BASE_DIR/Frontend"
MOBILE_DIR="$BASE_DIR/Mobile_React_Native"
JSON_DIR="$BASE_DIR/Json_Teste"
DATABASE_DIR="$BASE_DIR/Data_Base_tests"

mkdir -p "$BACKEND_DIR" "$FRONTEND_DIR" "$MOBILE_DIR" "$JSON_DIR" "$DATABASE_DIR"

echo "Projeto criado em: $BASE_DIR"

# ===============================
# Função para criar arquivos
# ===============================
cria_arquivo() {
    local file_path="$BACKEND_DIR/$1"
    mkdir -p "$(dirname "$file_path")"
    touch "$file_path"
    echo "Arquivo criado: $file_path"
}

# ===============================
# Backends
# ===============================
backend_js() {
    for file in \
        app/controller/HomeController.js \
        app/controller/UserController.js \
        app/controller/AuthController.js \
        app/model/UserModel.js \
        app/model/ProductModel.js \
        app/model/AuthModel.js \
        app/service/UserService.js \
        app/service/AuthService.js \
        app/service/ProductService.js \
        app/repository/UserRepository.js \
        app/repository/ProductRepository.js \
        app/middleware/auth.middleware.js \
        app/middleware/error.middleware.js \
        app/entity/UserEntity.js \
        app/entity/ProductEntity.js \
        app/dto/UserDTO.js \
        app/dto/AuthDTO.js \
        app/config/database.config.js \
        app/config/server.config.js \
        app/config/env.config.js \
        app/helpers/logger.helper.js \
        app/helpers/validator.helper.js \
        app/utils/crypto.util.js \
        app/utils/response.util.js \
        app/routes/index.routes.js \
        app/routes/user.routes.js \
        app/routes/auth.routes.js
    do
        cria_arquivo "$file"
    done
}

backend_ts() {
cat <<EOF > "$BACKEND_DIR/tsconfig.json"
{
  "compilerOptions": {
    "target": "ES6",
    "module": "CommonJS",
    "strict": true,
    "rootDir": "./app",
    "outDir": "./dist",
    "esModuleInterop": true
  }
}
EOF

    for file in \
        app/controller/HomeController.ts \
        app/controller/UserController.ts \
        app/controller/AuthController.ts \
        app/model/UserModel.ts \
        app/model/ProductModel.ts \
        app/model/AuthModel.ts \
        app/service/UserService.ts \
        app/service/AuthService.ts \
        app/service/ProductService.ts \
        app/repository/UserRepository.ts \
        app/repository/ProductRepository.ts \
        app/middleware/auth.middleware.ts \
        app/middleware/error.middleware.ts \
        app/entity/UserEntity.ts \
        app/entity/ProductEntity.ts \
        app/dto/UserDTO.ts \
        app/dto/AuthDTO.ts \
        app/config/database.config.ts \
        app/config/server.config.ts \
        app/config/env.config.ts \
        app/helpers/logger.helper.ts \
        app/helpers/validator.helper.ts \
        app/utils/crypto.util.ts \
        app/utils/response.util.ts \
        app/routes/index.routes.ts \
        app/routes/user.routes.ts \
        app/routes/auth.routes.ts
    do
        cria_arquivo "$file"
    done
}

backend_php() {
    for file in \
        app/controller/HomeController.php \
        app/controller/UserController.php \
        app/controller/AuthController.php \
        app/model/UserModel.php \
        app/model/ProductModel.php \
        app/model/AuthModel.php \
        app/service/UserService.php \
        app/service/AuthService.php \
        app/service/ProductService.php \
        app/repository/UserRepository.php \
        app/repository/ProductRepository.php \
        app/middleware/auth.middleware.php \
        app/middleware/error.middleware.php \
        app/entity/UserEntity.php \
        app/entity/ProductEntity.php \
        app/dto/UserDTO.php \
        app/dto/AuthDTO.php \
        app/config/database.config.php \
        app/config/server.config.php \
        app/config/env.config.php \
        app/helpers/logger.helper.php \
        app/helpers/validator.helper.php \
        app/utils/crypto.util.php \
        app/utils/response.util.php \
        app/routes/index.routes.php \
        app/routes/user.routes.php \
        app/routes/auth.routes.php
    do
        cria_arquivo "$file"
    done
}

# ================================
# Criar estrutura base
# ================================
create_base_folders() {
    for dir in controller model view service repository middleware entity dto \
               config helpers utils routes
    do
        mkdir -p "$BACKEND_DIR/app/$dir"
    done

    mkdir -p "$BACKEND_DIR/public" "$BACKEND_DIR/tests" \
             "$BACKEND_DIR/scripts" "$BACKEND_DIR/docs"

    touch "$BACKEND_DIR/.gitignore"
    touch "$BACKEND_DIR/.env"
}

# ==============
# MENUS
# ==============
main_menu() {
    echo ""
    echo "========= MENU PRINCIPAL ========="
    echo "1 | MVC"
    echo "2 | VANILLA | HTML | CSS | JS | Basic"
    echo "=================================="
    read -p "Escolha: " OPT_MAIN
}

sub_menu_mvc() {
    echo "========= MVC ========="
    echo "1 | Backend JS + Angular"
    echo "2 | Backend TS + Angular"
    read -p "Escolha: " OPT_MVC
}

sub_menu_vanila() {
    echo "========= VANILLA ========="
    echo "1 | PHP| Basic | Login | HomePage | Register HTML Basic"
    echo "2 | JS | Basic | Login | HomePage | Register HTML Basic"
    echo "3 | TS | Basic | Login | HomePage | Register HTML Basic"
    read -p "Escolha: " OPT_VAN
}

# ======================================
# JSON e Database Exemplo
# ======================================
create_data_json_for_test() {
cat <<EOF > "$JSON_DIR/test.json"
{
    "Name":"Name 1",
    "Age":19,
    "Country": "BR",
    "State": "SP",
    "City" :"City1"
}
EOF
}

create_database_for_teste(){
cat <<EOF > "$DATABASE_DIR/test.sql"
-- Database For testes
CREATE DATABASE teste;
USE teste;
CREATE TABLE teste1(
    id INT AUTO_INCREMENT PRIMARY KEY NOT NULL,
    name VARCHAR(100) NOT NULL,
    age INT NOT NULL,
    city VARCHAR(100) NOT NULL,
    country VARCHAR(100) NOT NULL
);
EOF
}

# ================================
# DEPENDÊNCIAS
# ================================
install_dependencies_1(){
  cd "$BACKEND_DIR" || exit
  npm init -y
  npm install express typeorm reflect-metadata mysql2 bcrypt jsonwebtoken dotenv cors passport passport-jwt class-validator class-transformer
  npm install -D typescript ts-node @types/node @types/express @types/jsonwebtoken @types/bcrypt @types/cors ts-node-dev
}

install_dependencies_2(){
  cd "$BACKEND_DIR" || exit
  npm init -y
  npm install @prisma/client
  npx prisma init
  npm install prisma reflect-metadata mysql2 bcrypt jsonwebtoken dotenv cors passport passport-jwt class-validator class-transformer
  npm install -D typescript ts-node @types/node @types/express @types/jsonwebtoken @types/bcrypt @types/cors ts-node-dev
}

# ================================
# React Native (Expo)
# ================================

cria_angular() {
    echo "🅰 Criando projeto Angular..."

    npm install -g @angular/cli

    cd "$FRONTEND_DIR"

    ng new Frontend_Angular --defaults --skip-git

    echo "✨ Angular criado em: $BASE_DIR/Frontend_Angular"
}


create_doc(){
    touch "$BACKEND_DIR/docs/README.md"
    touch "$BACKEND_DIR/docs/Version.md"
    touch "$BACKEND_DIR/docs/LICENSE.md"
    touch "$BACKEND_DIR/docs/CONTRIBUTING.md"
    touch "$BACKEND_DIR/docs/routes.md"
}

frontend_vanilla(){
    mkdir -p "$FRONTEND_DIR/assets/css"
    mkdir -p "$FRONTEND_DIR/assets/js"
    cat <<EOF >>"$FRONTEND_DIR/index.html"
    <!DOCTYPE html>
<html lang="pt-br">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Homepage</title>
    <link rel="stylesheet" href="../css/style.css">
    <link rel="shortcut icon" href="favicon.ico" type="image/x-icon">
    <script src=""></script>
</head>
<body>
    <nav>
        <ul>
            <li></li>
            <li></li>
            <li></li>
            <li></li>
            <li></li>
            <li></li>
            <li></li>
            <li></li>
        </ul>
    </nav>
    <main>
        <div></div>
        <div></div>
        <div></div>
        <div></div>
        <div></div>
        <div></div>
        <div></div>
    </main>
    <footer>
        <div></div>
        <div></div>
        <div></div>
    </footer>
</body>
</html>
EOF
cat <<EOF >>"$FRONTEND_DIR/login.html"
    <!DOCTYPE html>
<html lang="pt-br">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Login | Page</title>
    <link rel="stylesheet" href="../css/style.css">
    <link rel="shortcut icon" href="favicon.ico" type="image/x-icon">
    <script src=""></script>
</head>
<body>
    <nav>
        <ul>
            <li></li>
            <li></li>
            <li></li>
            <li></li>
            <li></li>
            <li></li>
            <li></li>
            <li></li>
        </ul>
    </nav>
    <main>
    <input type="text" placeholder="usuario">
    <input type="password" placeholder="password">
    </main>
    <footer>
        <div></div>
        <div></div>
        <div></div>
    </footer>
</body>
</html>
EOF
cat <<EOF >>"$FRONTEND_DIR/register.html"
    <!DOCTYPE html>
<html lang="pt-br">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Register | Page</title>
    <link rel="stylesheet" href="../css/style.css">
    <link rel="shortcut icon" href="favicon.ico" type="image/x-icon">
    <script src=""></script>
</head>
<body>
    <nav>
        <ul>
            <li></li>
            <li></li>
            <li></li>
            <li></li>
            <li></li>
            <li></li>
            <li></li>
            <li></li>
        </ul>
    </nav>
    <main>
    <input type="text" placeholder="usuario">
    <input type="password" placeholder="password">
    <input type="text">
    <input type="text">
    <input type="text">
    <input type="text">
    </main>
    <footer>
        <div></div>
        <div></div>
        <div></div>
    </footer>
</body>
</html>
EOF
cat <<EOF >"$FRONTEND_DIR/about.html"
<!DOCTYPE html>
<html lang="pt-br">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>About | Page</title>
    <link rel="stylesheet" href="../css/style.css">
    <link rel="shortcut icon" href="favicon.ico" type="image/x-icon">
</head>
<body>
    <nav>
        <ul>
            <li></li>
            <li></li>
            <li></li>
            <li></li>
            <li></li>
            <li></li>
            <li></li>
            <li></li>
        </ul>
    </nav>

    <main>
        <div></div>
        <div></div>
        <div></div>
        <div></div>
        <div></div>
        <div></div>
        <div></div>
    </main>

    <footer>
        <div></div>
        <div></div>
        <div></div>
    </footer>
</body>
</html>
EOF
cat <<EOF >"$FRONTEND_DIR/Products.html"
<!DOCTYPE html>
<html lang="pt-br">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>About | Page</title>
    <link rel="stylesheet" href="../css/style.css">
    <link rel="shortcut icon" href="favicon.ico" type="image/x-icon">
</head>
<body>
    <nav>
        <ul>
            <li></li>
            <li></li>
            <li></li>
            <li></li>
            <li></li>
            <li></li>
            <li></li>
            <li></li>
        </ul>
    </nav>

    <main>
        <!-- products.html -->
<nav></nav>

<main>
    <section id="products-list"></section>

    <section id="product-form"></section>

    <section id="product-details"></section>
</main>
    </main>

    <footer>
        <div></div>
        <div></div>
        <div></div>
    </footer>
</body>
</html>
EOF
cat <<EOF >"$FRONTEND_DIR/Contact.html"
<!DOCTYPE html>
<html lang="pt-br">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>About | Page</title>
    <link rel="stylesheet" href="../css/style.css">
    <link rel="shortcut icon" href="favicon.ico" type="image/x-icon">
</head>
<body>
    <nav>
        <ul>
            <li></li>
            <li></li>
            <li></li>
            <li></li>
            <li></li>
            <li></li>
            <li></li>
            <li></li>
        </ul>
    </nav>

    <main>
    <nav></nav>

<main>
    <section id="contact-form"></section>
    <section id="support-info"></section>
</main>
    </main>

    <footer>
        <div></div>
        <div></div>
        <div></div>
    </footer>
</body>
</html>
EOF
 cat <<EOF >>"$FRONTEND_DIR/assets/functions.js"
 //Functions for bootoms
function teste1(){}
function teste2(){}
function teste3(){}
function teste4(){}
function teste5(){}
EOF
 cat <<EOF >> "$BACKEND_DIR/server.js"
 // Import lib
const express = require('express')

// create instance express
const app = express()

// lib for json
app.use(express.json())

// Server Port
const PORT = 3000

//Routes for teste
app.get('/home',(req,res)=>{
    res.send('Homepage');
})
app.post('/home/login',(req,res)=>{
    res.send('Login Page');
})
app.get('/home/register',(req,res)=>{
    res.send('Register Page');
})
app.get('/home/contact',(req,res)=>{
    res.send('Contact Page');
})
app.get('/home/About',(req,res)=>{
    res.send('About Page');
})

// Function test (For register in JSON)
app.post('/usuarios',(req,res)=>{
   const novoUsuario = req.body;
   console.log("New User Register",novoUsuario)
   res.status(201).json({
    mensagem: "User Register Sucess",
    usuario: novoUsuario
   })
})
EOF
}



# ======================================
# CHAMADA DO MENU
# ======================================
main_menu

create_data_json_for_test
create_database_for_teste

echo "Script pronto! 🚀"

case $OPT_MAIN in

  # ==================== MVC ====================
  1)
    sub_menu_mvc
    case $OPT_MVC in
      1)
    create_base_folders
    backend_js
    cria_angular
    create_doc
      ;;
      2)
        create_base_folders
    backend_ts
    cria_angular
    create_doc
      ;;
      *)
        echo "Opção inválida no menu MVC"
      ;;
    esac
  ;;

  # ========== VANILLA ==========
  2)
    sub_menu_vanila
    case $OPT_VAN in
      1) backend_php; frontend_vanilla; create_doc ;;
      2) backend_js; frontend_vanilla; create_doc ;;
      3) backend_ts; frontend_vanilla; create_doc ;;
      *)
        echo "Opção inválida"
      ;;
    esac
  ;;
esac
```` 
