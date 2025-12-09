# 🌌 Constellation CLI

## Observação: `👁️Aceito Merenda ou Café se quiser`

## Menu
<p align="center">
  <img src="https://github.com/SidneiAJr/Documentacao/blob/main/prints/Captura%20de%20tela%202025-12-08%20133119.png">
</p>

---

## Estrutura de Pastas
<p align="center">
   <img src="https://github.com/SidneiAJr/Documentacao/blob/main/prints/Captura%20de%20tela%202025-12-08%20133140.png">
</p>

---
## Log Automaticamente Gerado
<p align="center">
   <img src="https://github.com/SidneiAJr/Documentacao/blob/main/prints/Captura%20de%20tela%202025-12-08%20133151.png">
</p>

## `Automação completa para criação de estruturas Frontend + Backend com MVC/MVVC`

## O Constellation CLI é uma ferramenta criada para acelerar a criação de projetos modernos, combinando duas ideias anteriores:

- Vapo Framework
- Vapo CLI

## A fusão dessas ideias deu origem ao Constellation, um CLI capaz de gerar projetos completos, organizados e escaláveis com um único comando.

- ✔ Estrutura completa de backend (JS / TS / PHP)
- ✔ Estrutura completa de frontend (React / Angular / Vanilla)
- ✔ Documentação automática
- ✔ Sistema de logs
- ✔ Arquivos base como controllers, models, services e muito mais
- ✔ Organização profissional de pastas
- ✔ Templates prontos para projetos MVC e MVVC

## 🧱 Tipos de Projeto Suportados
### MVC
- React + NodeJS + TypeScript
- Angular + NodeJS + JavaScript
- VanillaJS + PHP
### MVVC
- React + TypeScript
- Angular + JavaScript
- Angular + PHP

## 🧪 Log de Criação
### Gera automaticamente:
logs/constellation.log

Com:

- Estrutura criada
- Horário
- Tipo de arquitetura
- Mapas de diretórios
- Arquivos importantes
- Relatório 

### Script:

```bash
#!/bin/bash

clear
echo "=================================="
echo -e "  ██████╗ ██████╗ ███╗   ██╗███████╗███████╗
 ██╔════╝██╔═══██╗████╗  ██║██╔════╝██╔════╝
 ██║     ██║   ██║██╔██╗ ██║███████╗█████╗  
 ██║     ██║   ██║██║╚██╗██║╚════██║██╔══╝  
 ╚██████╗╚██████╔╝██║ ╚████║███████║███████╗
  ╚═════╝ ╚═════╝ ╚═╝  ╚═══╝╚══════╝╚══════╝

        ✨ C O N S T E L L A T I O N   C L I ✨

      WELCOME | THANKS FOR USE"
echo "=================================="
echo ""

# =============================================================
# PERGUNTA O NOME DO PROJETO
# =============================================================
read -p "Digite o nome do seu projeto: " PROJECT_NAME

BASE_DIR="$PROJECT_NAME"
BACKEND_DIR="$BASE_DIR/backend"
FRONTEND_DIR="$BASE_DIR/frontend"

mkdir -p "$BACKEND_DIR"
mkdir -p "$FRONTEND_DIR"

echo "Projeto criado em: $BASE_DIR"
echo ""

# ============================================================================
# MENU
# ============================================================================
menu() {
    echo "=================================="
    echo "                MENU"
    echo "=================================="
    echo "1 - MVC | React + NodeJS + TypeScript"
    echo "2 - MVC | Angular + NodeJS + JavaScript"
    echo "3 - MVC | Vanilla + PHP"
    echo "4 - MVVC | React + TypeScript"
    echo "5 - MVVC | Angular + JavaScript"
    echo "6 - MVVC | Angular + PHP"
    echo "0 - Sair"
    echo ""
}

# ============================================================================
# ESTRUTURA BASE BACKEND
# ============================================================================
cria_base() {
    for dir in controller model view service repository middleware entity dto \
               config helpers utils routes
    do
        mkdir -p "$BACKEND_DIR/app/$dir"
    done

    mkdir -p "$BACKEND_DIR/public"
    mkdir -p "$BACKEND_DIR/tests"
    mkdir -p "$BACKEND_DIR/scripts"
    mkdir -p "$BACKEND_DIR/docs"

    touch "$BACKEND_DIR/.gitignore"
    touch "$BACKEND_DIR/.env"
}

# ============================================================================
# FUNÇÃO PARA CRIAR ARQUIVOS
# ============================================================================
cria_arquivo() {
    mkdir -p "$(dirname "$BACKEND_DIR/$1")"
    touch "$BACKEND_DIR/$1"
}

# ============================================================================
# BACKENDS
# ============================================================================
backend_js(){
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

backend_ts(){
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

backend_php(){
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

# ============================================================================
# FRONTEND
# ============================================================================
frontend_react(){
    cd "$FRONTEND_DIR"
    npm create vite@latest react-app -- --template react-ts
    mv react-app/* . && rm -rf react-app
    npm install
    cd - > /dev/null
}

frontend_angular(){
    cd "$FRONTEND_DIR"
    ng new app --skip-git --minimal --style=css --routing=false
    mv app/* . && rm -rf app
    cd - > /dev/null
}

frontend_vanilla(){
    mkdir -p "$FRONTEND_DIR/assets/css"
    mkdir -p "$FRONTEND_DIR/assets/js"
    echo "<!DOCTYPE html><html><head><title>Vanilla</title></head><body><h1>Projeto Vanilla</h1><script src='assets/js/app.js'></script></body></html>" \
    > "$FRONTEND_DIR/index.html"
    touch "$FRONTEND_DIR/assets/js/app.js"
}

# ============================================================================
# EXECUÇÃO DO MENU
# ============================================================================
menu
read -p "Escolha uma opção: " OPCAO

cria_base

case $OPCAO in
    1)
        echo "Criando MVC | React + NodeJS + TypeScript..."
        backend_ts
        frontend_react
        ;;
    2)
        echo "Criando MVC | Angular + NodeJS + JavaScript..."
        backend_js
        frontend_angular
        ;;
    3)
        echo "Criando MVC | Vanilla + PHP..."
        backend_php
        frontend_vanilla
        ;;
    4)
        echo "Criando MVVC | React + TypeScript..."
        backend_ts
        frontend_react
        ;;
    5)
        echo "Criando MVVC | Angular + JavaScript..."
        backend_js
        frontend_angular
        ;;
    6)
        echo "Criando MVVC | Angular + PHP..."
        backend_php
        frontend_angular
        ;;
    0)
        echo "Saindo..."
        exit 0
        ;;
    *)
        echo "Opção inválida!"
        ;;
esac

echo ""
echo "✨ Projeto configurado com sucesso!"

# ============================================================================
# Gerador de Log | Criação do Projeto
# ============================================================================


gera_log() {
    mkdir -p "$BASE_DIR/logs"
    LOG_FILE="$BASE_DIR/logs/constellation.log"

    {
        echo "=============================================="
        echo "✨ Constellation CLI - Log de Criação de Projeto"
        echo "=============================================="
        echo "Projeto: $PROJECT_NAME"
        echo "Criado em: $(date '+%Y-%m-%d %H:%M:%S')"
        echo "Tipo selecionado: $PROJETO_ESCOLHIDO"
        echo ""
        echo "📁 Estrutura de Diretórios Criada:"
        echo "----------------------------------------------"
        
        echo "Backend:"
        tree "$BACKEND_DIR" 2>/dev/null || ls -R "$BACKEND_DIR"

        echo ""
        echo "Frontend:"
        tree "$FRONTEND_DIR" 2>/dev/null || ls -R "$FRONTEND_DIR"

        echo ""
        echo "📄 Arquivos importantes:"
        echo "----------------------------------------------"
        echo ".env              -> $BACKEND_DIR/.env"
        echo ".gitignore        -> $BACKEND_DIR/.gitignore"
        echo "Documentation/    -> $BASE_DIR/Documentation/"
        echo "Logs/             -> $BASE_DIR/logs/"
        echo ""
        echo "✨ Projeto configurado com sucesso!"
        echo "=============================================="
    
    } > "$LOG_FILE"
}


gera_documentation() {
    mkdir -p "$BASE_DIR/Documentation"

    DOC_FILE="$BASE_DIR/Documentation/README.md"
    DOC_FILE2="$BASE_DIR/Documentation/Version.md"
    DOC_FILE3="$BASE_DIR/Documentation/AboutProject.md"
    DOC_FILE5="$BASE_DIR/Documentation/CHANGELOG.md"
    DOC_FILE6="$BASE_DIR/Documentation/API.md"
    DOC_FILE7="$BASE_DIR/Documentation/CONTRIBUTING.md"
    DOC_FILE8="$BASE_DIR/Documentation/LICENSE.md"
    DOC_FILE9="$BASE_DIR/Documentation/ROADMAP.md"
    DOC_FILE10="$BASE_DIR/Documentation/SECURITY.md"
    DOC_FILE11="$BASE_DIR/Documentation/SketchIdeas.md"
    DOC_FILE12="$BASE_DIR/Documentation/Sketch.md"

    # cria os arquivos
    touch "$DOC_FILE" \
          "$DOC_FILE2" \
          "$DOC_FILE3" \
          "$DOC_FILE5" \
          "$DOC_FILE6" \
          "$DOC_FILE7" \
          "$DOC_FILE8" \
          "$DOC_FILE9" \
          "$DOC_FILE10" \
          "$DOC_FILE11" \
          "$DOC_FILE12"

    # limpa os arquivos
    : > "$DOC_FILE"
    : > "$DOC_FILE2"
    : > "$DOC_FILE3"
    : > "$DOC_FILE5"
    : > "$DOC_FILE6"
    : > "$DOC_FILE7"
    : > "$DOC_FILE8"
    : > "$DOC_FILE9"
    : > "$DOC_FILE10"
    : > "$DOC_FILE11"
    : > "$DOC_FILE12"

    echo "📚 Documentação criada em: $BASE_DIR/Documentation"


cat <<EOF >> "$BASE_DIR/Documentation/Sketch.md"
teste
EOF
    
}
gera_log
gera_documentation
````

## Nova Versão 0.03a | 🏗️ Em Desevolvimento | Cria Vanila em TS e JS

## Script:

````bash
#!/bin/bash

clear
echo "=================================="
echo -e "  ██████╗ ██████╗ ███╗   ██╗███████╗███████╗
          ██╔════╝██╔═══██╗████╗  ██║██╔════╝██╔════╝
          ██║     ██║   ██║██╔██╗ ██║███████╗█████╗  
          ██║     ██║   ██║██║╚██╗██║╚════██║██╔══╝  
           ╚██████╗╚██████╔╝██║ ╚████║███████║███████╗
            ╚═════╝ ╚═════╝ ╚═╝  ╚═══╝╚══════╝╚══════╝

        ✨ C O N S T E L L A T I O N   C L I ✨

      WELCOME | THANKS FOR USE"
echo "=================================="
echo ""

# =============================================================
# PERGUNTA O NOME DO PROJETO
# =============================================================
read -p "Digite o nome do seu projeto: " PROJECT_NAME

BASE_DIR="$PROJECT_NAME"
BACKEND_DIR="$BASE_DIR/backend"
FRONTEND_DIR="$BASE_DIR/frontend"

mkdir -p "$BACKEND_DIR"
mkdir -p "$FRONTEND_DIR"

echo "Projeto criado em: $BASE_DIR"
echo ""

# ============================================================================
# MENU
# ============================================================================
menu() {
    echo "=================================="
    echo "                MENU"
    echo "=================================="
    echo "1 - MVC | React + NodeJS + TypeScript"
    echo "2 - MVC | Angular + NodeJS + JavaScript"
    echo "3 - MVC | Vanilla + PHP"
    echo "4 - MVVC | React + TypeScript"
    echo "5 - MVVC | Angular + JavaScript"
    echo "6 - MVVC | Angular + PHP"
    echo "7 - MVVC | Vanila + JS | Backend JS"
    echo "8 - MVC | Vanila + JS | Backend JS"
    echo "9 - MVVC | Vanila + TS | Backend TS"
    echo "10 - MVC | Vanila + TS | Backend TS"
    echo "0 - Sair"
    echo ""
}

# ============================================================================
# ESTRUTURA BASE BACKEND
# ============================================================================
cria_base() {
    for dir in controller model view service repository middleware entity dto \
               config helpers utils routes
    do
        mkdir -p "$BACKEND_DIR/app/$dir"
    done

    mkdir -p "$BACKEND_DIR/public"
    mkdir -p "$BACKEND_DIR/tests"
    mkdir -p "$BACKEND_DIR/scripts"
    mkdir -p "$BACKEND_DIR/docs"

    touch "$BACKEND_DIR/.gitignore"
    touch "$BACKEND_DIR/.env"
}

# ============================================================================
# FUNÇÃO PARA CRIAR ARQUIVOS
# ============================================================================
cria_arquivo() {
    mkdir -p "$(dirname "$BACKEND_DIR/$1")"
    touch "$BACKEND_DIR/$1"
}

# ============================================================================
# BACKENDS
# ============================================================================
backend_js(){
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

backend_ts(){
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

backend_php(){
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

# ============================================================================
# FRONTEND
# ============================================================================
frontend_react(){
    cd "$FRONTEND_DIR"
    npm create vite@latest react-app -- --template react-ts
    mv react-app/* . && rm -rf react-app
    npm install
    cd - > /dev/null
}

frontend_angular(){
    cd "$FRONTEND_DIR"
    ng new app --skip-git --minimal --style=css --routing=false
    mv app/* . && rm -rf app
    cd - > /dev/null
}

frontend_vanilla(){
    mkdir -p "$FRONTEND_DIR/assets/css"
    mkdir -p "$FRONTEND_DIR/assets/js"
    echo "<!DOCTYPE html><html><head><title>Vanilla</title></head><body><h1>Projeto Vanilla</h1><script src='assets/js/app.js'></script></body></html>" \
    > "$FRONTEND_DIR/index.html"
    touch "$FRONTEND_DIR/assets/js/app.js"
}

# ============================================================================
# EXECUÇÃO DO MENU
# ============================================================================
menu
read -p "Escolha uma opção: " OPCAO

cria_base

case $OPCAO in
    1)
        echo "Criando MVC | React + NodeJS + TypeScript..."
        backend_ts
        frontend_react
        ;;
    2)
        echo "Criando MVC | Angular + NodeJS + JavaScript..."
        backend_js
        frontend_angular
        ;;
    3)
        echo "Criando MVC | Vanilla + PHP..."
        backend_php
        frontend_vanilla
        ;;
    4)
        echo "Criando MVVC | React + TypeScript..."
        backend_ts
        frontend_react
        ;;
    5)
        echo "Criando MVVC | Angular + JavaScript..."
        backend_js
        frontend_angular
        ;;
    6)
        echo "Criando MVVC | Angular + PHP..."
        backend_php
        frontend_angular
        ;;
    7) echo "Criando MVVC | Vanila + JS Backend..."
        backend_js
        frontend_vanilla
        ;;
    8) echo "Criando MVC| Vanila + JS Backend..."
        backend_js
        frontend_vanilla
        ;;
    9) echo "Criando MVVC| Vanila + TS Backend..."
        backend_ts
        frontend_vanilla
        ;;
    10) echo "Criando MVC| Vanila + TS Backend..."
        backend_ts
        frontend_vanilla
        ;;
       
    0)
        echo "Saindo..."
        exit 0
        ;;
    *)
        echo "Opção inválida!"
        ;;
esac

echo ""
echo "✨ Projeto configurado com sucesso!"

# ============================================================================
# Gerador de Log | Criação do Projeto
# ============================================================================


gera_log() {
    mkdir -p "$BASE_DIR/logs"
    LOG_FILE="$BASE_DIR/logs/constellation.log"

    {
        echo "=============================================="
        echo "✨ Constellation CLI - Log de Criação de Projeto"
        echo "=============================================="
        echo "Projeto: $PROJECT_NAME"
        echo "Criado em: $(date '+%Y-%m-%d %H:%M:%S')"
        echo "Tipo selecionado: $PROJETO_ESCOLHIDO"
        echo ""
        echo "📁 Estrutura de Diretórios Criada:"
        echo "----------------------------------------------"
        
        echo "Backend:"
        tree "$BACKEND_DIR" 2>/dev/null || ls -R "$BACKEND_DIR"

        echo ""
        echo "Frontend:"
        tree "$FRONTEND_DIR" 2>/dev/null || ls -R "$FRONTEND_DIR"

        echo ""
        echo "📄 Arquivos importantes:"
        echo "----------------------------------------------"
        echo ".env              -> $BACKEND_DIR/.env"
        echo ".gitignore        -> $BACKEND_DIR/.gitignore"
        echo "Documentation/    -> $BASE_DIR/Documentation/"
        echo "Logs/             -> $BASE_DIR/logs/"
        echo ""
        echo "✨ Projeto configurado com sucesso!"
        echo "=============================================="
    
    } > "$LOG_FILE"
}


gera_documentation() {
    mkdir -p "$BASE_DIR/Documentation"

    DOC_FILE="$BASE_DIR/Documentation/README.md"
    DOC_FILE2="$BASE_DIR/Documentation/Version.md"
    DOC_FILE3="$BASE_DIR/Documentation/AboutProject.md"
    DOC_FILE5="$BASE_DIR/Documentation/CHANGELOG.md"
    DOC_FILE6="$BASE_DIR/Documentation/API.md"
    DOC_FILE7="$BASE_DIR/Documentation/CONTRIBUTING.md"
    DOC_FILE8="$BASE_DIR/Documentation/LICENSE.md"
    DOC_FILE9="$BASE_DIR/Documentation/ROADMAP.md"
    DOC_FILE10="$BASE_DIR/Documentation/SECURITY.md"
    DOC_FILE11="$BASE_DIR/Documentation/SketchIdeas.md"
    DOC_FILE12="$BASE_DIR/Documentation/Sketch.md"

    # cria os arquivos
    touch "$DOC_FILE" \
          "$DOC_FILE2" \
          "$DOC_FILE3" \
          "$DOC_FILE5" \
          "$DOC_FILE6" \
          "$DOC_FILE7" \
          "$DOC_FILE8" \
          "$DOC_FILE9" \
          "$DOC_FILE10" \
          "$DOC_FILE11" \
          "$DOC_FILE12"

    # limpa os arquivos
    : > "$DOC_FILE"
    : > "$DOC_FILE2"
    : > "$DOC_FILE3"
    : > "$DOC_FILE5"
    : > "$DOC_FILE6"
    : > "$DOC_FILE7"
    : > "$DOC_FILE8"
    : > "$DOC_FILE9"
    : > "$DOC_FILE10"
    : > "$DOC_FILE11"
    : > "$DOC_FILE12"

    echo "📚 Documentação criada em: $BASE_DIR/Documentation"


cat <<EOF >> "$BASE_DIR/Documentation/Sketch.md"
teste
EOF
    
}
gera_log
gera_documentation
````




