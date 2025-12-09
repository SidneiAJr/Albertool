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
    <p>Bem-vindo ao seu portfólio gerado automaticamente!</p>
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
