# 📜 Gerador de HTML Básico — v0.2 Alpha

Um script em Shell Script criado para automatizar a geração de projetos HTML — desde estruturas simples até templates completos com CSS, lógica PHP e documentação.

Perfeito para quem quer iniciar projetos rapidamente sem perder tempo montando pastas e arquivos toda vez.

# 📸 Preview do Menu
<p align="center"> <img src="https://github.com/SidneiAJr/Documentacao/blob/main/prints/Captura%20de%20tela%202025-12-07%20175918.png?raw=true" width="700"> </p>

## ⚙️ Recursos disponíveis

A versão 0.2 Alpha A do gerador oferece:

## 🟦 Template 1 – HTML Simples

index.html

script.js

Estrutura limpa

Sem CSS (ideal para protótipos rápidos)

## 🟩 Template 2 – HTML Completo (sem backend)

CSS + JS organizados

Pastas: img/, js/, logic/, documentation/

Páginas: index, login, register

Arquivos PHP iniciais (opcional)

## 🟧 Template 3 – HTML + Bootstrap

Estrutura pronta com:

Bootstrap via CDN

Layout responsivo

Arquivos base para começar imediatamente

## 🟨 Template 4 – HTML + Tailwind CSS

Configuração pré-montada

Estrutura pronta para estilização rápida

## 🟪 Template 5 – Portfólio HTML

Base para portfolio pessoal

Estrutura moderna

Seções pré-criadas

## 🟥 Template 6 – Estrutura HTML sem CSS

HTML5 + organização base

Ideal para aulas, testes ou frameworks

## 🟫 Template 7 – HTML + CSS pronto

Layout pré-formatado

CSS funcional junto do HTML

Design básico já incluído
---

## 🚀 Como usar
1️⃣ Crie uma pasta vazia

Ela será o destino final da estrutura do template.

2️⃣ Dentro dela, crie um arquivo de texto

Pode ser gerador.txt, htmltool.txt, qualquer nome.

3️⃣ Cole o script do gerador

O código da versão 0.2 Alpha A.

4️⃣ Salve como .sh

5️⃣ Rodar o .sh

## Script Abaixo:

````bash
#!/bin/bash

# ===========================================================
#          AlberTool – HTML Project Generator v0.2 Alpha A
# ===========================================================

clear
echo "==============================================="
echo "        🚀 AlberTool — HTML Generator"
echo "              Versão 0.2 Alpha A"
echo "==============================================="
echo ""

echo "Escolha o tipo de template:"
echo "1) HTML Simples (Sem CSS)"
echo "2) HTML Completo (CSS + JS + Login/Register)"
echo "3) HTML + Bootstrap"
echo "4) HTML + Tailwind"
echo "5) Template Portfólio"
echo "6) HTML Estrutura Montada (somente HTML)"
echo "7) HTML Estrutura + CSS Básico"
echo ""

read -p "Opção: " OP
read -p "Nome do projeto: " PROJ

mkdir -p "$PROJ"

# ===========================================================
# FUNÇÃO - Criar Estrutura Padrão
# ===========================================================
criar_base() {
    local base=$1

    mkdir -p "$base/img"
    mkdir -p "$base/js"
    mkdir -p "$base/css"
    mkdir -p "$base/logic"
    mkdir -p "$base/documentation"

    # HTML Base
    cat <<EOF > $base/index.html
<!DOCTYPE html>
<html>
<head>
    <title>$PROJ</title>
    <meta charset="UTF-8">
</head>
<body>
    <h1>Projeto $PROJ criado pelo AlberTool v0.2</h1>
</body>
</html>
EOF

    # JS Base
    echo "// Script gerado automaticamente" > $base/js/script.js

    # CSS Base
    echo "/* CSS gerado automaticamente */" > $base/css/style.css

    # Documentação
    echo "# Documentação do Projeto $PROJ" > $base/documentation/README.md
}

# ===========================================================
# FUNÇÃO - Criar arquivos PHP (login, register, list, conex)
# ===========================================================
criar_php() {
    local base=$1

    # login.php
    cat <<EOF > $base/logic/login.php
<?php
echo "login.php funcionando!";
?>
EOF

    # register.php
    cat <<EOF > $base/logic/register.php
<?php
echo "register.php funcionando!";
?>
EOF

    # list.php
    cat <<EOF > $base/logic/list.php
<?php
echo "list.php funcionando!";
?>
EOF

    # conex.php
    cat <<EOF > $base/logic/conex.php
<?php
try {
    \$pdo = new PDO("mysql:host=localhost;dbname=test","root","");
    echo "Conexão bem-sucedida!";
} catch (PDOException \$e) {
    echo "Erro: " . \$e->getMessage();
}
?>
EOF
}

# ===========================================================
# TEMPLATE 1 — HTML Simples
# ===========================================================
if [ "$OP" == "1" ]; then
    BASE="$PROJ/html_simples"
    mkdir -p "$BASE"
    criar_base "$BASE"
fi

# ===========================================================
# TEMPLATE 2 — HTML Completo (com login + register)
# ===========================================================
if [ "$OP" == "2" ]; then
    BASE="$PROJ/html_completo"
    mkdir -p "$BASE"
    criar_base "$BASE"
    criar_php "$BASE"
fi

# ===========================================================
# TEMPLATE 3 — Bootstrap
# ===========================================================
if [ "$OP" == "3" ]; then
    BASE="$PROJ/html_bootstrap"
    mkdir -p "$BASE"
    criar_base "$BASE"
    criar_php "$BASE"

    # adicionar bootstrap no HTML
    sed -i 's|</head>|<link rel="stylesheet" href="https://cdn.jsdelivr.net/npm/bootstrap@5.3.2/dist/css/bootstrap.min.css"></head>|' $BASE/index.html
fi

# ===========================================================
# TEMPLATE 4 — Tailwind
# ===========================================================
if [ "$OP" == "4" ]; then
    BASE="$PROJ/html_tailwind"
    mkdir -p "$BASE"
    criar_base "$BASE"
    criar_php "$BASE"

    sed -i 's|</head>|<script src="https://cdn.tailwindcss.com"></script></head>|' $BASE/index.html
fi

# ===========================================================
# TEMPLATE 5 — Portfólio
# ===========================================================
if [ "$OP" == "5" ]; then
    BASE="$PROJ/portfolio"
    mkdir -p "$BASE"
    criar_base "$BASE"

cat <<EOF > $BASE/index.html
<!DOCTYPE html>
<html>
<head>
    <title>Portfólio — $PROJ</title>
    <meta charset="UTF-8">
</head>
<body>
    <h1>$PROJ</h1>
    <p>Bem-vindo ao seu portfólio !</p>
</body>
</html>
EOF
fi

# ===========================================================
# TEMPLATE 6 — Estrutura HTML pura
# ===========================================================
if [ "$OP" == "6" ]; then
    BASE="$PROJ/html_puro"
    mkdir -p "$BASE"
    criar_base "$BASE"
fi

# ===========================================================
# TEMPLATE 7 — HTML + CSS pronto
# ===========================================================
if [ "$OP" == "7" ]; then
    BASE="$PROJ/html_css"
    mkdir -p "$BASE"
    criar_base "$BASE"

    echo "body { font-family: Arial; background: #f0f0f0; }" > $BASE/css/style.css
fi

# ===========================================================
echo ""
echo "==============================================="
echo " ✔ Projeto '$PROJ' criado com sucesso!"
echo " ✔ Versão: AlberTool HTML Generator v0.2 Alpha A"
echo "==============================================="
````

## Projeto na versão Alpha Qualquer coisa entrar em contato!


## New Version:

```bash
#!/bin/bash
echo ==================================================
echo Welcome HTML Generator Base Basic No MVC or MVVC
echo Pay me Coffe More Affter
echo Coffe in Brasil is GOLD
echo ==================================================

BASE_DIR="./project"

create_folder_base(){
    mkdir -p "$BASE_DIR/css"
    mkdir -p "$BASE_DIR/js"
    mkdir -p "$BASE_DIR/Backend"
    mkdir -p "$BASE_DIR/Frontend"
	mkdir -p "$BASE_DIR/documentation"
}

menu(){
    echo ==================================================
	echo Welcome HTML Generator Base Basic No MVC or MVVC
    echo ==================================================
    echo "1 | HTML Basic| Login | Homepage | Register | About | Contact + PHP | Basic Project"
    echo "2 | HTML Bootstrap| Login | Homepage | Register | About | Contact + JS | Basic Project"
    echo "3 | HTML Tailwind | Login | Homepage | Register | About | Contact + TS | Basic Project"
}

main_menu(){
    while true; do
        clear
        menu
        read op

        case $op in
            1)
                create_folder_base
                create_html_archive
				create_backend_php
				create_documetion
				create_js_archives
                echo "✔ HTML + PHP!"
                ;;
            2)
                create_folder_base
                create_html_bootsrap_base
				create_backend_js
				create_documetion
				create_js_archives
                echo "✔ HTML + JS!"
                ;;
            3)
                create_folder_base
                create_html_tailwind
				create_backend_ts
				create_documetion
				create_js_archives
                echo "✔ HTML + TS!"
                ;;
            *)
                echo "❌ Opção inválida!"
                ;;
        esac

        echo ""
        read -p "Pressione ENTER para voltar ao menu..."
    done
}

create_js_archives(){
  cat <<EOF >"$BASE_DIR/js/functions.js"
  //functions 
  function(){}
  function(){}
  function(){}
  function(){}
  function(){}
  function(){}
  function(){}
  function(){}
  function(){}
  function(){}
  function(){}
  function(){}
  function(){}
  function(){}
  function(){}
  function(){}
  function(){}
  function(){}
  function(){}
  function(){}
EOF

}

create_documetion(){
    touch "$BASE_DIR/documentation/Readme.md"
    touch "$BASE_DIR/documentation/LICENCE.md"
    touch "$BASE_DIR/documentation/HELP.md"
    touch "$BASE_DIR/documentation/routes.md"
    touch "$BASE_DIR/documentation/Struture.md"
    touch "$BASE_DIR/documentation/CONTRIBUTING.md"
}

create_backend_php(){
    touch "$BASE_DIR/Backend/index.php"
    touch "$BASE_DIR/Backend/login.php"
    touch "$BASE_DIR/Backend/contact.php"
    touch "$BASE_DIR/Backend/form.php"
}

create_backend_js(){
    touch "$BASE_DIR/Backend/index.js"
    touch "$BASE_DIR/Backend/login.js"
    touch "$BASE_DIR/Backend/contact.js"
    touch "$BASE_DIR/Backend/form.js"
    cat <<EOF >"$BASE_DIR/Backend/server.js"
    const express = require('express')
const mysql = require('mysql2')
const app = express()
app.use(express.json())
const connection = mysql.createConnection({
    host: 'localhost', // Host
    port: 3306, // Porta
    user : '', // usuario
    password : '', // senha
    database: '' // Nome Banco
})
connection.connect()
app.post('/usuarios',(req,res)=>{
    const {}=req.body
    const comandobanco = "INSERT INTO  () values(?,?)"
    connection.query(comandobanco,[],(erro)=>{
         if(erro){
          return res.status(500).send("Erro ao adicionar usuario!")
         }
         return res.status(201).send("Usuario Adicionado com sucesso!")
    })
})
app.get('/ler',(req,res)=>{
    const leitura = "SELECT * FROM ";
     connection.query(leitura,(erro,resultado)=>{
         if(erro){
          return res.status(500).send("Erro | Leitura nâo Realizada")
         }
         res.status(200).json(resultado)

    })
})
app.get('/ler/:id',(req,res)=>{
    const {id}= req.params
    const leitura = "SELECT * from  where id = ?";
     connection.query(leitura,[],(erro,resultado)=>{
         if(erro){
          return res.status(500).send("Erro | Leitura nâo Realizada")
         }
         res.status(200).json(resultado)
    })
})
app.put('/at/:id',(req,res)=>{
    const {} = req.params
    const {} = req.body
    const atualizao = "Update  set nome = ?,email = ? where id = ?";
     connection.query(atualizao,[],(erro,resultado)=>{
         if(erro){
          return res.status(500).send("Erro | ao tentar atualizar o usuario")
         }
         res.status(200).send("Usuario Atualizado com sucesso!!!")
    })
})
app.delete('/deletar/:id',(req,res)=>{
    const {id} = req.params
    const atualizao = "delete from  where id = ?";
     connection.query(atualizao,[],(erro,resultado)=>{
         if(erro){
          return res.status(500).send("Erro | ao tentar deletar usuario")
         }
         res.status(200).send("Usuario Deletado com sucesso!!!")
    })
})
const port = 3000
app.listen(port,()=>{
    console.log(`Servidor Rodando localhost:${port}`)
})
EOF
}

create_backend_ts(){
    touch "$BASE_DIR/Backend/index.ts"
    touch "$BASE_DIR/Backend/login.ts"
    touch "$BASE_DIR/Backend/contact.ts"
    touch "$BASE_DIR/Backend/form.ts"
    touch "$BASE_DIR/Backend/form2.ts"
    
}

create_html_archive(){
    cat <<EOF >"$BASE_DIR/Frontend/index.html"
<!DOCTYPE html>
<html lang="pt-br">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>HomePage</title>
    <script src=""></script>
    <link rel="stylesheet" href="">
    <link href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.0.0-beta3/css/all.min.css" rel="stylesheet">
</head>
<body>
    <nav>
        <ul>
            <li><a href="register.html"><i class="fas fa-user-plus"></i> Register</a></li>
            <li><a href="login.html"><i class="fas fa-sign-in-alt"></i> Login</a></li>
            <li><a href="about.html"><i class="fas fa-info-circle"></i> About</a></li>
            <li><a href="contacts.html"><i class="fas fa-address-book"></i> Contacts</a></li>
        </ul>
    </nav>
    <main>
        <div>Hello</div>
        <div>Hello</div>
        <div>Hello</div>
        <div>Hello</div>
        <div>Hello</div>
        <p></p>
    </main>
    <footer>
        <div></div>
        <div></div>
        <div></div>
        <div></div>
    </footer>
</body>
</html>
EOF
cat <<EOF >"$BASE_DIR/Frontend/login.html"
<!DOCTYPE html>
<html lang="pt-br">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Login</title>
    <script src=""></script>
    <link rel="stylesheet" href="">
    <link href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.0.0-beta3/css/all.min.css" rel="stylesheet">
</head>
<body>
    <nav>
        <ul>
            <li><a href="register.html"><i class="fas fa-user-plus"></i> Register</a></li>
            <li><a href="login.html"><i class="fas fa-sign-in-alt"></i> Login</a></li>
            <li><a href="about.html"><i class="fas fa-info-circle"></i> About</a></li>
            <li><a href="contacts.html"><i class="fas fa-address-book"></i> Contacts</a></li>
        </ul>
    </nav>
    <main>
        <h2>Login</h2>
        <form action="process_login.php" method="POST">
            <label for="username">Username:</label>
            <input type="text" id="username" name="username" required>
            <br>
            <label for="password">Password:</label>
            <input type="password" id="password" name="password" required>
            <br>
            <button type="submit"><i class="fas fa-sign-in-alt"></i> Login</button>
        </form>
        <p>Don't have an account? <a href="register.html">Register here</a></p>
    </main>
    <footer>
        <div></div>
        <div></div>
        <div></div>
        <div></div>
    </footer>
</body>
</html>
EOF
cat <<EOF >"$BASE_DIR/Frontend/register.html"
<!DOCTYPE html>
<html lang="pt-br">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Register</title>
    <script src=""></script>
    <link rel="stylesheet" href="">
    <link href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.0.0-beta3/css/all.min.css" rel="stylesheet">
</head>
<body>
    <nav>
        <ul>
            <li><a href="register.html"><i class="fas fa-user-plus"></i> Register</a></li>
            <li><a href="login.html"><i class="fas fa-sign-in-alt"></i> Login</a></li>
            <li><a href="about.html"><i class="fas fa-info-circle"></i> About</a></li>
            <li><a href="contacts.html"><i class="fas fa-address-book"></i> Contacts</a></li>
        </ul>
    </nav>
    <main>
        <h2>Register</h2>
        <form action="process_register.php" method="POST">
            <label for="username">Username:</label>
            <input type="text" id="username" name="username" required>
            <br>
            <label for="email">Email:</label>
            <input type="email" id="email" name="email" required>
            <br>
            <label for="password">Password:</label>
            <input type="password" id="password" name="password" required>
            <br>
            <label for="confirm_password">Confirm Password:</label>
            <input type="password" id="confirm_password" name="confirm_password" required>
            <br>
            <button type="submit"><i class="fas fa-user-plus"></i> Register</button>
        </form>
        <p>Already have an account? <a href="login.html">Login here</a></p>
    </main>
    <footer>
        <div></div>
        <div></div>
        <div></div>
        <div></div>
    </footer>
</body>
</html>
EOF
cat <<EOF >"$BASE_DIR/Frontend/About.html"
<!DOCTYPE html>
<html lang="pt-br">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>About</title>
    <script src=""></script>
    <link rel="stylesheet" href="">
    <link href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.0.0-beta3/css/all.min.css" rel="stylesheet">
</head>
<body>
    <nav>
        <ul>
            <li><a href="register.html"><i class="fas fa-user-plus"></i> Register</a></li>
            <li><a href="login.html"><i class="fas fa-sign-in-alt"></i> Login</a></li>
            <li><a href="about.html"><i class="fas fa-info-circle"></i> About</a></li>
            <li><a href="contacts.html"><i class="fas fa-address-book"></i> Contacts</a></li>
        </ul>
    </nav>
    <main>
        <h2>About Us</h2>
        <p></p>
        <h3></h3>
        <ul>
            <li></li>
            <li></li>
            <li></li>
        </ul>
    </main>
    <footer>
        <div></div>
        <div></div>
        <div></div>
        <div></div>
    </footer>
</body>
</html>
EOF
cat <<EOF >"$BASE_DIR/Frontend/contacts.html"
<!DOCTYPE html>
<html lang="pt-br">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Contacts</title>
    <script src=""></script>
    <link rel="stylesheet" href="">
    <link href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.0.0-beta3/css/all.min.css" rel="stylesheet">
</head>
<body>
    <nav>
        <ul>
            <li><a href="register.html"><i class="fas fa-user-plus"></i> Register</a></li>
            <li><a href="login.html"><i class="fas fa-sign-in-alt"></i> Login</a></li>
            <li><a href="about.html"><i class="fas fa-info-circle"></i> About</a></li>
            <li><a href="contacts.html"><i class="fas fa-address-book"></i> Contacts</a></li>
        </ul>
    </nav>
    <main>
        <h2>Contact Us</h2>
        <p>Lorem ipsum dolor sit amet, consectetur adipiscing elit. Integer nec odio. Praesent libero. Sed cursus ante dapibus diam. Sed nisi.</p>

        <h3>Email:</h3>
        <p>Lorem ipsum dolor sit amet, consectetur adipiscing elit. Integer nec odio. Praesent libero. Sed cursus ante dapibus diam. Sed nisi.</p>

        <h3>Phone:</h3>
        <p>Lorem ipsum dolor sit amet, consectetur adipiscing elit. Integer nec odio. Praesent libero. Sed cursus ante dapibus diam. Sed nisi.</p>

        <h3>Address:</h3>
        <p>Lorem ipsum dolor sit amet, consectetur adipiscing elit. Integer nec odio. Praesent libero. Sed cursus ante dapibus diam. Sed nisi.</p>

        <h3>Follow Us:</h3>
        <ul>
            <li><a href="https://facebook.com/ourwebsite" target="_blank"><i class="fab fa-facebook"></i> Facebook</a></li>
            <li><a href="https://twitter.com/ourwebsite" target="_blank"><i class="fab fa-twitter"></i> Twitter</a></li>
            <li><a href="https://instagram.com/ourwebsite" target="_blank"><i class="fab fa-instagram"></i> Instagram</a></li>
        </ul>
    </main>
    <footer>
        <div></div>
        <div></div>
        <div></div>
        <div></div>
    </footer>
</body>
</html>
EOF
}

create_html_bootsrap_base(){
    cat <<EOF >"$BASE_DIR/Frontend/index.html"
<!DOCTYPE html>
<html lang="pt-br">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>HomePage</title>
    <link href="https://cdn.jsdelivr.net/npm/bootstrap@5.3.0-alpha1/dist/css/bootstrap.min.css" rel="stylesheet">
    <link href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.0.0-beta3/css/all.min.css" rel="stylesheet">
</head>
<body>
    <nav class="navbar navbar-expand-lg navbar-light bg-light">
        <div class="container-fluid">
            <a class="navbar-brand" href="#">Website</a>
            <button class="navbar-toggler" type="button" data-bs-toggle="collapse" data-bs-target="#navbarNav" aria-controls="navbarNav" aria-expanded="false" aria-label="Toggle navigation">
                <span class="navbar-toggler-icon"></span>
            </button>
            <div class="collapse navbar-collapse" id="navbarNav">
                <ul class="navbar-nav">
                    <li class="nav-item"><a class="nav-link" href="register.html"><i class="fas fa-user-plus"></i> Register</a></li>
                    <li class="nav-item"><a class="nav-link" href="login.html"><i class="fas fa-sign-in-alt"></i> Login</a></li>
                    <li class="nav-item"><a class="nav-link" href="about.html"><i class="fas fa-info-circle"></i> About</a></li>
                    <li class="nav-item"><a class="nav-link" href="contacts.html"><i class="fas fa-address-book"></i> Contacts</a></li>
                </ul>
            </div>
        </div>
    </nav>
    <main class="container mt-5">
        <div class="row">
            <div class="col">
                <h2>Welcome to Our Website</h2>
                <p>Lorem ipsum dolor sit amet, consectetur adipiscing elit. Integer nec odio. Praesent libero. Sed cursus ante dapibus diam. Sed nisi.</p>
            </div>
        </div>
    </main>
    <footer class="bg-light text-center py-3">
        <p>&copy; 2025 Website, All Rights Reserved</p>
    </footer>
    <script src="https://cdn.jsdelivr.net/npm/bootstrap@5.3.0-alpha1/dist/js/bootstrap.bundle.min.js"></script>
</body>
</html>
EOF

    cat <<EOF >"$BASE_DIR/Frontend/login.html"
<!DOCTYPE html>
<html lang="pt-br">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Login</title>
    <link href="https://cdn.jsdelivr.net/npm/bootstrap@5.3.0-alpha1/dist/css/bootstrap.min.css" rel="stylesheet">
    <link href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.0.0-beta3/css/all.min.css" rel="stylesheet">
</head>
<body>
    <nav class="navbar navbar-expand-lg navbar-light bg-light">
        <div class="container-fluid">
            <a class="navbar-brand" href="#">Website</a>
            <button class="navbar-toggler" type="button" data-bs-toggle="collapse" data-bs-target="#navbarNav" aria-controls="navbarNav" aria-expanded="false" aria-label="Toggle navigation">
                <span class="navbar-toggler-icon"></span>
            </button>
            <div class="collapse navbar-collapse" id="navbarNav">
                <ul class="navbar-nav">
                    <li class="nav-item"><a class="nav-link" href="register.html"><i class="fas fa-user-plus"></i> Register</a></li>
                    <li class="nav-item"><a class="nav-link" href="login.html"><i class="fas fa-sign-in-alt"></i> Login</a></li>
                    <li class="nav-item"><a class="nav-link" href="about.html"><i class="fas fa-info-circle"></i> About</a></li>
                    <li class="nav-item"><a class="nav-link" href="contacts.html"><i class="fas fa-address-book"></i> Contacts</a></li>
                </ul>
            </div>
        </div>
    </nav>
    <main class="container mt-5">
        <h2>Login</h2>
        <form action="process_login.php" method="POST">
            <div class="mb-3">
                <label for="username" class="form-label">Username</label>
                <input type="text" class="form-control" id="username" name="username" required>
            </div>
            <div class="mb-3">
                <label for="password" class="form-label">Password</label>
                <input type="password" class="form-control" id="password" name="password" required>
            </div>
            <button type="submit" class="btn btn-primary"><i class="fas fa-sign-in-alt"></i> Login</button>
        </form>
        <p class="mt-3">Don't have an account? <a href="register.html">Register here</a></p>
    </main>
    <footer class="bg-light text-center py-3">
        <p>&copy; 2025 Website, All Rights Reserved</p>
    </footer>
    <script src="https://cdn.jsdelivr.net/npm/bootstrap@5.3.0-alpha1/dist/js/bootstrap.bundle.min.js"></script>
</body>
</html>
EOF

    cat <<EOF >"$BASE_DIR/Frontend/register.html"
<!DOCTYPE html>
<html lang="pt-br">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Register</title>
    <link href="https://cdn.jsdelivr.net/npm/bootstrap@5.3.0-alpha1/dist/css/bootstrap.min.css" rel="stylesheet">
    <link href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.0.0-beta3/css/all.min.css" rel="stylesheet">
</head>
<body>
    <nav class="navbar navbar-expand-lg navbar-light bg-light">
        <div class="container-fluid">
            <a class="navbar-brand" href="#">Website</a>
            <button class="navbar-toggler" type="button" data-bs-toggle="collapse" data-bs-target="#navbarNav" aria-controls="navbarNav" aria-expanded="false" aria-label="Toggle navigation">
                <span class="navbar-toggler-icon"></span>
            </button>
            <div class="collapse navbar-collapse" id="navbarNav">
                <ul class="navbar-nav">
                    <li class="nav-item"><a class="nav-link" href="register.html"><i class="fas fa-user-plus"></i> Register</a></li>
                    <li class="nav-item"><a class="nav-link" href="login.html"><i class="fas fa-sign-in-alt"></i> Login</a></li>
                    <li class="nav-item"><a class="nav-link" href="about.html"><i class="fas fa-info-circle"></i> About</a></li>
                    <li class="nav-item"><a class="nav-link" href="contacts.html"><i class="fas fa-address-book"></i> Contacts</a></li>
                </ul>
            </div>
        </div>
    </nav>
    <main class="container mt-5">
        <h2>Register</h2>
        <form action="process_register.php" method="POST">
            <div class="mb-3">
                <label for="username" class="form-label">Username</label>
                <input type="text" class="form-control" id="username" name="username" required>
            </div>
            <div class="mb-3">
                <label for="email" class="form-label">Email</label>
                <input type="email" class="form-control" id="email" name="email" required>
            </div>
            <div class="mb-3">
                <label for="password" class="form-label">Password</label>
                <input type="password" class="form-control" id="password" name="password" required>
            </div>
            <div class="mb-3">
                <label for="confirm_password" class="form-label">Confirm Password</label>
                <input type="password" class="form-control" id="confirm_password" name="confirm_password" required>
            </div>
            <button type="submit" class="btn btn-primary"><i class="fas fa-user-plus"></i> Register</button>
        </form>
        <p class="mt-3">Already have an account? <a href="login.html">Login here</a></p>
    </main>
    <footer class="bg-light text-center py-3">
        <p>&copy; 2025 Website, All Rights Reserved</p>
    </footer>
    <script src="https://cdn.jsdelivr.net/npm/bootstrap@5.3.0-alpha1/dist/js/bootstrap.bundle.min.js"></script>
</body>
</html>
EOF

    cat <<EOF >"$BASE_DIR/Frontend/About.html"
<!DOCTYPE html>
<html lang="pt-br">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>About</title>
    <link href="https://cdn.jsdelivr.net/npm/bootstrap@5.3.0-alpha1/dist/css/bootstrap.min.css" rel="stylesheet">
    <link href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.0.0-beta3/css/all.min.css" rel="stylesheet">
</head>
<body>
    <nav class="navbar navbar-expand-lg navbar-light bg-light">
        <div class="container-fluid">
            <a class="navbar-brand" href="#">Website</a>
            <button class="navbar-toggler" type="button" data-bs-toggle="collapse" data-bs-target="#navbarNav" aria-controls="navbarNav" aria-expanded="false" aria-label="Toggle navigation">
                <span class="navbar-toggler-icon"></span>
            </button>
            <div class="collapse navbar-collapse" id="navbarNav">
                <ul class="navbar-nav">
                    <li class="nav-item"><a class="nav-link" href="register.html"><i class="fas fa-user-plus"></i> Register</a></li>
                    <li class="nav-item"><a class="nav-link" href="login.html"><i class="fas fa-sign-in-alt"></i> Login</a></li>
                    <li class="nav-item"><a class="nav-link" href="about.html"><i class="fas fa-info-circle"></i> About</a></li>
                    <li class="nav-item"><a class="nav-link" href="contacts.html"><i class="fas fa-address-book"></i> Contacts</a></li>
                </ul>
            </div>
        </div>
    </nav>
    <main class="container mt-5">
        <h2>About Us</h2>
        <p>Lorem ipsum dolor sit amet, consectetur adipiscing elit. Integer nec odio. Praesent libero. Sed cursus ante dapibus diam. Sed nisi.</p>
    </main>
    <footer class="bg-light text-center py-3">
        <p>&copy; 2025 Website, All Rights Reserved</p>
    </footer>
    <script src="https://cdn.jsdelivr.net/npm/bootstrap@5.3.0-alpha1/dist/js/bootstrap.bundle.min.js"></script>
</body>
</html>
EOF

    cat <<EOF >"$BASE_DIR/Frontend/contacts.html"
<!DOCTYPE html>
<html lang="pt-br">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Contacts</title>
    <link href="https://cdn.jsdelivr.net/npm/bootstrap@5.3.0-alpha1/dist/css/bootstrap.min.css" rel="stylesheet">
    <link href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.0.0-beta3/css/all.min.css" rel="stylesheet">
</head>
<body>
    <nav class="navbar navbar-expand-lg navbar-light bg-light">
        <div class="container-fluid">
            <a class="navbar-brand" href="#">Website</a>
            <button class="navbar-toggler" type="button" data-bs-toggle="collapse" data-bs-target="#navbarNav" aria-controls="navbarNav" aria-expanded="false" aria-label="Toggle navigation">
                <span class="navbar-toggler-icon"></span>
            </button>
            <div class="collapse navbar-collapse" id="navbarNav">
                <ul class="navbar-nav">
                    <li class="nav-item"><a class="nav-link" href="register.html"><i class="fas fa-user-plus"></i> Register</a></li>
                    <li class="nav-item"><a class="nav-link" href="login.html"><i class="fas fa-sign-in-alt"></i> Login</a></li>
                    <li class="nav-item"><a class="nav-link" href="about.html"><i class="fas fa-info-circle"></i> About</a></li>
                    <li class="nav-item"><a class="nav-link" href="contacts.html"><i class="fas fa-address-book"></i> Contacts</a></li>
                </ul>
            </div>
        </div>
    </nav>
    <main class="container mt-5">
        <h2>Contact Us</h2>
        <p>Lorem ipsum dolor sit amet, consectetur adipiscing elit. Integer nec odio. Praesent libero. Sed cursus ante dapibus diam. Sed nisi.</p>

        <h3>Email:</h3>
        <p>Lorem ipsum dolor sit amet, consectetur adipiscing elit. Integer nec odio. Praesent libero. Sed cursus ante dapibus diam. Sed nisi.</p>

        <h3>Phone:</h3>
        <p>Lorem ipsum dolor sit amet, consectetur adipiscing elit. Integer nec odio. Praesent libero. Sed cursus ante dapibus diam. Sed nisi.</p>

        <h3>Address:</h3>
        <p>Lorem ipsum dolor sit amet, consectetur adipiscing elit. Integer nec odio. Praesent libero. Sed cursus ante dapibus diam. Sed nisi.</p>

        <h3>Follow Us:</h3>
        <ul>
            <li><a href="https://facebook.com" target="_blank"><i class="fab fa-facebook"></i> Facebook</a></li>
            <li><a href="https://twitter.com" target="_blank"><i class="fab fa-twitter"></i> Twitter</a></li>
            <li><a href="https://instagram.com" target="_blank"><i class="fab fa-instagram"></i> Instagram</a></li>
        </ul>
    </main>
    <footer class="bg-light text-center py-3">
        <p>&copy; 2025 Website, All Rights Reserved</p>
    </footer>
    <script src="https://cdn.jsdelivr.net/npm/bootstrap@5.3.0-alpha1/dist/js/bootstrap.bundle.min.js"></script>
</body>
</html>
EOF
}

create_html_tailwind(){
    cat <<EOF >"$BASE_DIR/Frontend/index.html"
<!DOCTYPE html>
<html lang="pt-br">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>HomePage</title>
    <script src="https://cdn.tailwindcss.com"></script>
    <link href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.0.0-beta3/css/all.min.css" rel="stylesheet">
</head>
<body class="bg-gray-100">

    <nav class="bg-blue-500 p-4">
        <div class="max-w-7xl mx-auto flex justify-between items-center">
            <a href="#" class="text-white text-lg font-bold">Website</a>
            <ul class="flex space-x-6 text-white">
                <li><a href="register.html"><i class="fas fa-user-plus"></i> Register</a></li>
                <li><a href="login.html"><i class="fas fa-sign-in-alt"></i> Login</a></li>
                <li><a href="about.html"><i class="fas fa-info-circle"></i> About</a></li>
                <li><a href="contacts.html"><i class="fas fa-address-book"></i> Contacts</a></li>
            </ul>
        </div>
    </nav>

    <main class="max-w-7xl mx-auto mt-8 p-4">
        <h2 class="text-2xl font-bold text-gray-900">Welcome to Our Website</h2>
        <p class="text-gray-600 mt-2">Lorem ipsum dolor sit amet, consectetur adipiscing elit. Integer nec odio. Praesent libero. Sed cursus ante dapibus diam. Sed nisi.</p>
    </main>

    <footer class="bg-gray-200 text-center py-4 mt-8">
        <p>&copy; 2025 Website, All Rights Reserved</p>
    </footer>

</body>
</html>
EOF

    cat <<EOF >"$BASE_DIR/Frontend/login.html"
<!DOCTYPE html>
<html lang="pt-br">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Login</title>
    <script src="https://cdn.tailwindcss.com"></script>
    <link href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.0.0-beta3/css/all.min.css" rel="stylesheet">
</head>
<body class="bg-gray-100">

    <nav class="bg-blue-500 p-4">
        <div class="max-w-7xl mx-auto flex justify-between items-center">
            <a href="#" class="text-white text-lg font-bold">Website</a>
            <ul class="flex space-x-6 text-white">
                <li><a href="register.html"><i class="fas fa-user-plus"></i> Register</a></li>
                <li><a href="login.html"><i class="fas fa-sign-in-alt"></i> Login</a></li>
                <li><a href="about.html"><i class="fas fa-info-circle"></i> About</a></li>
                <li><a href="contacts.html"><i class="fas fa-address-book"></i> Contacts</a></li>
            </ul>
        </div>
    </nav>

    <main class="max-w-7xl mx-auto mt-8 p-4">
        <h2 class="text-2xl font-bold text-gray-900">Login</h2>
        <form action="process_login.php" method="POST" class="mt-4 space-y-4">
            <div class="flex flex-col">
                <label for="username" class="text-gray-700">Username</label>
                <input type="text" id="username" name="username" class="p-2 border border-gray-300 rounded" required>
            </div>
            <div class="flex flex-col">
                <label for="password" class="text-gray-700">Password</label>
                <input type="password" id="password" name="password" class="p-2 border border-gray-300 rounded" required>
            </div>
            <button type="submit" class="w-full bg-blue-500 text-white p-2 rounded mt-4"><i class="fas fa-sign-in-alt"></i> Login</button>
        </form>
        <p class="mt-4">Don't have an account? <a href="register.html" class="text-blue-500">Register here</a></p>
    </main>

    <footer class="bg-gray-200 text-center py-4 mt-8">
        <p>&copy; 2025 Website, All Rights Reserved</p>
    </footer>

</body>
</html>
EOF

    cat <<EOF >"$BASE_DIR/Frontend/register.html"
<!DOCTYPE html>
<html lang="pt-br">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Register</title>
    <script src="https://cdn.tailwindcss.com"></script>
    <link href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.0.0-beta3/css/all.min.css" rel="stylesheet">
</head>
<body class="bg-gray-100">

    <nav class="bg-blue-500 p-4">
        <div class="max-w-7xl mx-auto flex justify-between items-center">
            <a href="#" class="text-white text-lg font-bold">Website</a>
            <ul class="flex space-x-6 text-white">
                <li><a href="register.html"><i class="fas fa-user-plus"></i> Register</a></li>
                <li><a href="login.html"><i class="fas fa-sign-in-alt"></i> Login</a></li>
                <li><a href="about.html"><i class="fas fa-info-circle"></i> About</a></li>
                <li><a href="contacts.html"><i class="fas fa-address-book"></i> Contacts</a></li>
            </ul>
        </div>
    </nav>

    <main class="max-w-7xl mx-auto mt-8 p-4">
        <h2 class="text-2xl font-bold text-gray-900">Register</h2>
        <form action="process_register.php" method="POST" class="mt-4 space-y-4">
            <div class="flex flex-col">
                <label for="username" class="text-gray-700">Username</label>
                <input type="text" id="username" name="username" class="p-2 border border-gray-300 rounded" required>
            </div>
            <div class="flex flex-col">
                <label for="email" class="text-gray-700">Email</label>
                <input type="email" id="email" name="email" class="p-2 border border-gray-300 rounded" required>
            </div>
            <div class="flex flex-col">
                <label for="password" class="text-gray-700">Password</label>
                <input type="password" id="password" name="password" class="p-2 border border-gray-300 rounded" required>
            </div>
            <div class="flex flex-col">
                <label for="confirm_password" class="text-gray-700">Confirm Password</label>
                <input type="password" id="confirm_password" name="confirm_password" class="p-2 border border-gray-300 rounded" required>
            </div>
            <button type="submit" class="w-full bg-blue-500 text-white p-2 rounded mt-4"><i class="fas fa-user-plus"></i> Register</button>
        </form>
        <p class="mt-4">Already have an account? <a href="login.html" class="text-blue-500">Login here</a></p>
    </main>

    <footer class="bg-gray-200 text-center py-4 mt-8">
        <p>&copy; 2025 Website, All Rights Reserved</p>
    </footer>

</body>
</html>
EOF

    cat <<EOF >"$BASE_DIR/Frontend/About.html"
<!DOCTYPE html>
<html lang="pt-br">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>About</title>
    <script src="https://cdn.tailwindcss.com"></script>
    <link href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.0.0-beta3/css/all.min.css" rel="stylesheet">
</head>
<body class="bg-gray-100">

    <nav class="bg-blue-500 p-4">
        <div class="max-w-7xl mx-auto flex justify-between items-center">
            <a href="#" class="text-white text-lg font-bold">Website</a>
            <ul class="flex space-x-6 text-white">
                <li><a href="register.html"><i class="fas fa-user-plus"></i> Register</a></li>
                <li><a href="login.html"><i class="fas fa-sign-in-alt"></i> Login</a></li>
                <li><a href="about.html"><i class="fas fa-info-circle"></i> About</a></li>
                <li><a href="contacts.html"><i class="fas fa-address-book"></i> Contacts</a></li>
            </ul>
        </div>
    </nav>

    <main class="max-w-7xl mx-auto mt-8 p-4">
        <h2 class="text-2xl font-bold text-gray-900">About Us</h2>
        <p class="text-gray-600 mt-2">Lorem ipsum dolor sit amet, consectetur adipiscing elit. Integer nec odio. Praesent libero. Sed cursus ante dapibus diam. Sed nisi.</p>
    </main>

    <footer class="bg-gray-200 text-center py-4 mt-8">
        <p>&copy; 2025 Website, All Rights Reserved</p>
    </footer>

</body>
</html>
EOF

    cat <<EOF >"$BASE_DIR/Frontend/contacts.html"
<!DOCTYPE html>
<html lang="pt-br">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Contacts</title>
    <script src="https://cdn.tailwindcss.com"></script>
    <link href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.0.0-beta3/css/all.min.css" rel="stylesheet">
</head>
<body class="bg-gray-100">

    <nav class="bg-blue-500 p-4">
        <div class="max-w-7xl mx-auto flex justify-between items-center">
            <a href="#" class="text-white text-lg font-bold">Website</a>
            <ul class="flex space-x-6 text-white">
                <li><a href="register.html"><i class="fas fa-user-plus"></i> Register</a></li>
                <li><a href="login.html"><i class="fas fa-sign-in-alt"></i> Login</a></li>
                <li><a href="about.html"><i class="fas fa-info-circle"></i> About</a></li>
                <li><a href="contacts.html"><i class="fas fa-address-book"></i> Contacts</a></li>
            </ul>
        </div>
    </nav>

    <main class="max-w-7xl mx-auto mt-8 p-4">
        <h2 class="text-2xl font-bold text-gray-900">Contact Us</h2>
        <p class="text-gray-600 mt-2">Lorem ipsum dolor sit amet, consectetur adipiscing elit. Integer nec odio. Praesent libero. Sed cursus ante dapibus diam. Sed nisi.</p>

        <h3 class="text-lg font-semibold mt-4">Email:</h3>
        <p class="text-gray-600">Lorem ipsum dolor sit amet, consectetur adipiscing elit.</p>

        <h3 class="text-lg font-semibold mt-4">Phone:</h3>
        <p class="text-gray-600">Lorem ipsum dolor sit amet, consectetur adipiscing elit.</p>

        <h3 class="text-lg font-semibold mt-4">Address:</h3>
        <p class="text-gray-600">Lorem ipsum dolor sit amet, consectetur adipiscing elit.</p>

        <h3 class="text-lg font-semibold mt-4">Follow Us:</h3>
        <ul>
            <li><a href="https://facebook.com" class="text-blue-500"><i class="fab fa-facebook"></i> Facebook</a></li>
            <li><a href="https://twitter.com" class="text-blue-500"><i class="fab fa-twitter"></i> Twitter</a></li>
            <li><a href="https://instagram.com" class="text-blue-500"><i class="fab fa-instagram"></i> Instagram</a></li>
        </ul>
    </main>

    <footer class="bg-gray-200 text-center py-4 mt-8">
        <p>&copy; 2025 Website, All Rights Reserved</p>
    </footer>

</body>
</html>
EOF
}

main_menu
````
