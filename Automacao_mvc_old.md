# 🐘PHP| TS | MVC Pastas:

## `Script automático para criação de projeto MVC (PHP + TypeScript)`:

Este repositório contém um script .bat que cria automaticamente uma estrutura completa de projeto MVC, incluindo pastas, arquivos e organização para desenvolvimento com PHP e TypeScript.

Ideal para quem quer iniciar projetos rapidamente com uma arquitetura organizada e escalável.
Só usar e torrar 😄🔥

## 📜Script de criação (Batch | .bat)

````Shell
@echo off
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

:: Vendor (composer irá povoar depois)
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


````
## 📁 `Estrutura MVC — Explicação Completa (Sem Código)`

Abaixo está o significado de cada pasta e arquivo da sua estrutura MVC.

## Nível Principal
app/

Contém toda a lógica da aplicação.
Aqui ficam Controllers, Models e Views, que são as três camadas principais do padrão MVC.

## 📁Camada Controller
app/Controllers/

Armazena os controladores da aplicação.
Eles são responsáveis por:

receber requisições do usuário

decidir o que fazer

chamar Models (dados)

chamar Views (interface)

Exemplos: ProductController, UserController.

## 📁Camada Model
app/Models/

Contém as classes que trabalham com os dados da aplicação.

Os Models:

representam tabelas ou entidades

fazem consultas ao banco

lidam com regras de negócio relacionadas a dados

Exemplos: Product, User.

## 📁Camada View
app/Views/

Guarda as telas e arquivos de interface do usuário.

Aqui ficam:

páginas HTML/PHP exibidas no navegador

templates

layouts

pastas separadas por módulo (ex.: product, user)

## 📁Core do Sistema
core/

É o núcleo do seu mini-framework MVC.
Aqui ficam classes que fazem tudo funcionar.

Funções principais:

iniciar a aplicação

controlar o roteamento

renderizar views

fornecer classe base para Controllers

fornecer classe base para Models

Arquivos como App, Router, Controller, Model e View pertencem aqui.

## 📁Configurações
config/

Contém arquivos de configuração global da aplicação.

Aqui você define:

conexão com banco

rotas do sistema

opções gerais do app

configurações de ambiente

Exemplos: database.php, routes.php, app.php.

## 📁Helpers
helpers/

Contém funções auxiliares, utilitárias e não relacionadas a nenhuma camada específica.

São usadas para:

manipular sessões

formatar dados

realizar pequenas tarefas comuns

## 📁Services
services/

A camada Service serve para colocar lógicas mais complexas que não pertencem diretamente a um Controller ou Model.

Usado para:

regras de negócio pesadas

cálculos

orquestração de processos

validações mais elaboradas

Exemplos: UserService, ProductService.

## 📁Middleware
middleware/

Executa ações antes ou depois de uma requisição chegar ao Controller.

Exemplos de responsabilidades:

autenticação (ver se o usuário está logado)

proteção contra CSRF

controle de acesso

filtros de requisição

## 📁Pasta Pública
public/

É a única pasta acessível diretamente pelo navegador.

Aqui ficam:

index.php (ponto de entrada da aplicação)

CSS

JavaScript

imagens

arquivos TypeScript/JS do frontend

páginas públicas (ex.: erro 404)

Essa pasta é servida pelo Apache/Nginx.

## 📁Storage
storage/

Armazena tudo o que o sistema grava automaticamente.

Subpastas comuns:

logs/ → para logs da aplicação

uploads/ → arquivos enviados pelo usuário

cache/ → dados temporários para melhorar performance

## 📁Vendor
vendor/

Criada automaticamente pelo Composer.
Armazena todas as bibliotecas externas e dependências do seu projeto.

## Arquivos Raiz
.env

Variáveis sensíveis do ambiente, como:

senha do banco

chave de API

modo debug

.gitignore

Define quais arquivos/pastas não devem ir para o repositório.

composer.json

Arquivo principal do Composer:

lista dependências

define configurações da aplicação

README.md

Documentação do projeto.

| Pasta / Arquivo   | Função                                      |
| ----------------- | ------------------------------------------- |
| **app/**          | Lógica da aplicação                         |
| app/Controllers   | Controladores (recebem requisições)         |
| app/Models        | Dados e regras de negócios                  |
| app/Views         | Interface e telas                           |
| **core/**         | Núcleo do MVC (roteamento, base de classes) |
| **config/**       | Configurações globais                       |
| **helpers/**      | Funções auxiliares                          |
| **services/**     | Regras de negócio complexas                 |
| **middleware/**   | Filtros e autenticação                      |
| **public/**       | Arquivos acessíveis pela web                |
| **storage/**      | Logs, uploads e cache                       |
| **vendor/**       | Dependências externas                       |
| **.env**          | Configurações sensíveis                     |
| **composer.json** | Dependências do Composer                    |
