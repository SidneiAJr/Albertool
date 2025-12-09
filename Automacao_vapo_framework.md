# ⚡ VAPO Framework — CLI de Automação para Front-End, Estruturas MVC e Templates

O VAPO Framework é um gerador de projetos experimental desenvolvido em Batch Script (Windows).
Ele automatiza criação de estruturas completas, templates HTML, projetos em frameworks modernos e até setups MVC completos, tudo via terminal.

Criado para quem quer agilidade, organização e produtividade.

## 🧪 Versão experimental — evolução contínua.

Este documento acompanha o script principal de automação:

## 🚀 O que o VAPO é capaz de criar?
## ✔ Estrutura base de projeto

Padrão de pastas organizado, pronto para iniciar qualquer aplicação web.

## ✔  Templates HTML

Gera templates com HTML, CSS e JS automaticamente.

## ✔ Controllers, Models e Views

Cria arquivos isolados para organizar projetos de forma escalável.

## ✔ Documentação automática

Gera arquivos .md essenciais para documentação profissional.

## ✔ Estrutura MVC completa

Arquitetura robusta com pastas de:

Controllers

Models

Views

Core

Helpers

Middleware

Config

Storage

Public

Vendor

Além de arquivos .php, .ts e .html criados automaticamente.

## ✔ Criação de projetos React

Usando Create React App (via npx).

## ✔ Criação de projetos Angular

Com Angular CLI, incluindo routing + CSS + instalação automática.

## 📜 Menu:
```bash
1 - Criar Estrutura Base do Projeto
2 - Criar Template HTML
3 - Criar Controller
4 - Criar Model
5 - Criar View
6 - Criar Documentacao
7 - Criar Estrutura MVC COMPLETA
8 - Criar Projeto React
9 - Criar Projeto Angular
0 - Sair
````
---

## Script:

````bash
@echo off
title VAPO Framework - CLI Oficial

:menu
cls
echo ============================================
echo        V A P O   F R A M E W O R K
echo ============================================
echo 1 - Criar Estrutura Base do Projeto
echo 2 - Criar Template HTML
echo 3 - Criar Controller
echo 4 - Criar Model
echo 5 - Criar View
echo 6 - Criar Documentacao
echo 7 - Criar Estrutura MVC COMPLETA
echo 8 - Criar Projeto React
echo 9 - Criar Projeto Angular
echo 0 - Sair
echo ============================================
set /p opc="Escolha uma opcao: "

if "%opc%"=="1" goto estrutura
if "%opc%"=="2" goto template
if "%opc%"=="3" goto controller
if "%opc%"=="4" goto model
if "%opc%"=="5" goto view
if "%opc%"=="6" goto docs
if "%opc%"=="7" goto mvcfull
if "%opc%"=="8" goto react
if "%opc%"=="9" goto angular
if "%opc%"=="0" exit
goto menu
:: ============================
:angular
cls
echo ==============================
echo Criar Projeto Angular
echo ==============================
set /p aname="Nome do projeto Angular: "

where node >nul 2>&1 || (
    echo ERRO: Node.js nao encontrado.
    pause
    goto menu
)

echo Criando projeto Angular usando npx...
npx @angular/cli new %aname% --routing --style=css --skip-install

if %errorlevel% neq 0 (
    echo ERRO: Falha ao criar projeto Angular.
    pause
    goto menu
)

cd %aname%
echo Instalando dependencias...
npm install
cd ..

echo Projeto Angular criado com sucesso!
pause
goto menu

:: ============================
:react
cls
echo ==============================
echo Criar Projeto React
echo ==============================
set /p rname="Nome do projeto React: "
echo Criando projeto React %rname% ...
npx create-react-app %rname%
echo Projeto React criado!
pause
goto menu

:: ============================
:estrutura
echo Criando estrutura do VAPO...
mkdir templates
mkdir templates\default
mkdir templates\default\img

mkdir public
mkdir public\css
mkdir public\js
mkdir public\img

mkdir app
mkdir app\views
mkdir app\controllers
mkdir app\models

echo Estrutura criada com sucesso!
pause
goto menu

:: ============================
:template
set /p tname="Nome do novo template: "
mkdir templates\%tname%
mkdir templates\%tname%\img

> templates\%tname%\index.html echo <!DOCTYPE html^>
>> templates\%tname%\index.html echo ^<html lang="pt-BR"^>
>> templates\%tname%\index.html echo ^<head^>
>> templates\%tname%\index.html echo     ^<meta charset="UTF-8"^>
>> templates\%tname%\index.html echo     ^<title^>{{title}}^</title^>
>> templates\%tname%\index.html echo     ^<link rel="stylesheet" href="/css/style.css"^>
>> templates\%tname%\index.html echo ^</head^>
>> templates\%tname%\index.html echo ^<body^>
>> templates\%tname%\index.html echo     ^<h1^>{{title}} TEMPLATE %tname%^</h1^>
>> templates\%tname%\index.html echo ^</body^>
>> templates\%tname%\index.html echo ^</html^>

> templates\%tname%\style.css echo body { background:#222; color:#fff; }

> templates\%tname%\script.js echo console.log("Template %tname% carregado!");

echo Template %tname% criado!
pause
goto menu

:: ============================
:controller
set /p cname="Nome do controller: "
> app\controllers\%cname%Controller.ts echo export class %cname%Controller { }
echo Controller criado!
pause
goto menu

:: ============================
:model
set /p mname="Nome do model: "
> app\models\%mname%.ts echo export class %mname% { }
echo Model criado!
pause
goto menu

:: ============================
:view
set /p vname="Nome da view: "
> app\views\%vname%.html echo ^<h1^>View %vname%^</h1^>
echo View criada!
pause
goto menu

:: ============================
:docs
echo Criando documentacao...
mkdir documentacao

type nul > documentacao\Version.md
type nul > documentacao\Readme.md
type nul > documentacao\Information.md
type nul > documentacao\Struture.md
type nul > documentacao\About.md
type nul > documentacao\Route.md
type nul > documentacao\SketchI.md
type nul > documentacao\SketchII.md

echo Documentacao criada!
pause
goto menu

:: ============================
:: ESTRUTURA MVC COMPLETA
:mvcfull
cls
echo ==============================
echo Criando estrutura MVC Completa...
echo ==============================

:: Pastas principais
md app
md app\Controllers
md app\Models
md app\Views
md app\Views\product
md app\Views\user

:: Camadas adicionais
md core
md helpers
md services
md middleware

:: Storage
md storage
md storage\logs
md storage\uploads
md storage\cache

:: Public
md public
md public\css
md public\js
md public\img
md public\ts

:: Config
md config

:: Vendor
md vendor

echo ==============================
echo Criando arquivos iniciais...
echo ==============================

:: Arquivos root
type nul > .env
type nul > .gitignore
type nul > composer.json
type nul > README.md

:: Core
type nul > core\App.php
type nul > core\Controller.php
type nul > core\Model.php
type nul > core\View.php
type nul > core\Router.php
type nul > core\App.ts
type nul > core\Controller.ts
type nul > core\Model.ts
type nul > core\View.ts
type nul > core\Router.ts

:: Controllers
type nul > app\Controllers\ProductController.php
type nul > app\Controllers\UserController.php
type nul > app\Controllers\ProductController.ts
type nul > app\Controllers\UserController.ts

:: Models
type nul > app\Models\Product.php
type nul > app\Models\User.php
type nul > app\Models\Product.ts
type nul > app\Models\User.ts

:: Views
type nul > app\Views\product\index.php
type nul > app\Views\product\show.php
type nul > app\Views\user\index.php
type nul > app\Views\user\profile.php
type nul > app\Views\layout.php
type nul > app\Views\product\index.ts
type nul > app\Views\product\show.ts
type nul > app\Views\user\index.ts
type nul > app\Views\user\profile.ts
type nul > app\Views\layout.ts

:: Helpers
type nul > helpers\functions.php
type nul > helpers\session.php
type nul > helpers\functions.ts
type nul > helpers\session.ts

:: Services
type nul > services\UserService.php
type nul > services\ProductService.php
type nul > services\UserService.ts
type nul > services\ProductService.ts

:: Middleware
type nul > middleware\AuthMiddleware.php
type nul > middleware\CsrfMiddleware.php
type nul > middleware\AuthMiddleware.ts
type nul > middleware\CsrfMiddleware.ts

:: Config
type nul > config\database.php
type nul > config\routes.php
type nul > config\app.php
type nul > config\database.ts
type nul > config\routes.ts
type nul > config\app.ts

:: Public
type nul > public\index.php
type nul > public\404.php
type nul > public\css\style.css
type nul > public\js\app.js
type nul > public\ts\main.ts

:: Storage
type nul > storage\logs\app.log

echo ==============================
echo Estrutura COMPLETA criada!
echo ==============================
pause
goto menu
````
