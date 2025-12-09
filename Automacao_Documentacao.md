# 📜 Automação | Gerador de Documentação

Um pequeno automator criado para gerar rapidamente uma estrutura padrão de documentação para qualquer projeto.
Ideal para organizar versões, informações, rotas, esboços e detalhes internos — tudo com um único clique.

## 🧩 O que o script cria?

Ao executar o .bat, ele gera automaticamente a pasta:

### `documentacao/`

E dentro dela, os seguintes arquivos:

- Version.md — Informações de versão e changelog

- Readme.md — Descrição base do projeto

- Information.md — Informações gerais

- Structure.md — Estrutura do projeto

- About.md — Sobre o projeto

- Route.md — Rotas / endpoints

- sketch_I.md — Esboço 1

- sketch_II.md — Esboço 2

Tudo pronto para preencher e documentar. ✔️

## 🖥️ Como usar?

### 1️⃣ Crie um arquivo de texto

### 2️⃣ Cole o código acima

### 3️⃣ Salve como:

gerar_docs.bat

### 4️⃣ Dê dois cliques no arquivo

### 5️⃣ VAPO 💨 — sua estrutura de documentação está pronta!
 
````bash
@echo off
title Gerador de Documentação
color 0a

echo ================================
echo    Criando Documentação Base
echo ================================

:: Criar pasta
mkdir documentacao

:: Criar arquivos dentro da pasta
type nul > documentacao\Version.md
type nul > documentacao\Readme.md
type nul > documentacao\Information.md
type nul > documentacao\Structure.md
type nul > documentacao\About.md
type nul > documentacao\Route.md
type nul > documentacao\sketch_I.md
type nul > documentacao\sketch_II.md

echo.
echo Documentação criada com sucesso!
echo.
pause
````
