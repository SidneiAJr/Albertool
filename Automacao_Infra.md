# 📜 Automação | Monitoramento de Infraestrutura Windows

### Um script em Batch (.bat) para monitoramento rápido e simples de servidores, portas, DNS, internet e sites — tudo em tempo real, direto do CMD.

- Ideal para:

- Admins de TI

- DevOps iniciantes

- Estudantes de redes

- Suporte técnico

- Automação de ambientes locais

## 🧠 O que esse script faz?

✔ Verifica se o servidor está online

✔ Reinicia automaticamente um serviço se a porta cair

✔ Testa internet via ping (8.8.8.8)

✔ Testa acesso a qualquer site (HTTP HEAD)

✔ Registra tudo em log (monitor_log.txt)

✔ Funciona em qualquer Windows

## 🔍 Funções do Script

- 🔹 1. Monitorar servidor e reiniciar se cair

Você informa o IP ou domínio

Ele faz ping contínuo

Se cair → salva no log + dispara ação de restart

(Você pode personalizar o restart do seu serviço)

- 🔹 2. Monitorar porta + reiniciar serviço

Verifica se a porta existe via netstat

Se não existir → reinicia o serviço informado

- 🔹 3. Teste rápido de internet

Ping no DNS do Google (8.8.8.8)

- 🔹 4. Testar acesso a site

Usa curl para testar resposta HTTP

Funciona mesmo sem navegador

````bash
@echo off
title Monitor de Servidor - Automação Turbo
color 0A

:: ====== CAMINHO DO LOG ======
set LOG=monitor_log.txt

:MENU
cls
echo ============================================
echo         Monitor de Servidor / Rede
echo ============================================
echo.
echo [1] Monitorar servidor e reiniciar se cair
echo [2] Monitorar porta e reiniciar serviço
echo [3] Testar internet (Ping 8.8.8.8)
echo [4] Testar acesso a site (google.com)
echo [0] Sair
echo.
set /p opc=Escolha uma opcao: 

if "%opc%"=="1" goto MONITOR_SERVER
if "%opc%"=="2" goto MONITOR_PORT
if "%opc%"=="3" goto PING_TEST
if "%opc%"=="4" goto SITE_TEST
if "%opc%"=="0" exit
goto MENU


:: ============================================================
:: 1 — MONITORAR SERVIDOR E REINICIAR SE CAIR
:: ============================================================
:MONITOR_SERVER
cls
echo --------------------------------------------
echo MONITORANDO SERVIDOR...
echo --------------------------------------------
echo.
set /p host=Digite o IP ou dominio do servidor: 

echo Monitorando servidor %host%...
echo Pressione CTRL + C para parar.
timeout /t 2 >nul

:LOOP_SERVER
ping -n 1 %host% >nul
if errorlevel 1 (
    echo [%date% %time%] Servidor %host% caiu! >> %LOG%
    echo Servidor caiu! Reiniciando...
    :: coloque aqui o comando que reinicia seu servidor
    :: exemplo: net stop MeuServidor ^& net start MeuServidor
) else (
    echo Servidor Online: %host%
)

timeout /t 3 >nul
goto LOOP_SERVER


:: ============================================================
:: 2 — MONITORAR PORTA E REINICIAR SERVIÇO
:: ============================================================
:MONITOR_PORT
cls
echo --------------------------------------------
echo MONITORAR PORTA
echo --------------------------------------------
echo.

set /p porta=Digite a porta a monitorar: 
set /p servico=Digite o nome do servico para reiniciar: 

echo Monitorando porta %porta%...
timeout /t 2 >nul

:LOOP_PORT
netstat -ano | find ":%porta%" >nul
if errorlevel 1 (
    echo [%date% %time%] Porta %porta% offline! Restart do serviço >> %LOG%
    echo Porta %porta% offline... Reiniciando serviço %servico%...
    net stop "%servico%" >nul
    net start "%servico%" >nul
) else (
    echo Porta %porta% OK!
)

timeout /t 3 >nul
goto LOOP_PORT


:: ============================================================
:: 3 — TESTE DE INTERNET (PING 8.8.8.8)
:: ============================================================
:PING_TEST
cls
echo Testando conexão com a internet...
echo.

ping 8.8.8.8 -n 1 >nul
if errorlevel 1 (
    echo Sem internet!
    echo [%date% %time%] Falha no ping ao DNS >> %LOG%
) else (
    echo Internet OK!
)

pause
goto MENU


:: ============================================================
:: 4 — TESTAR ACESSO A SITE
:: ============================================================
:SITE_TEST
cls
echo Testar acesso a site
echo.

set /p URL=Digite um site (ex: google.com): 

curl -Is %URL% >nul 2>&1
if errorlevel 1 (
    echo Site inacessível!
    echo [%date% %time%] Falha ao acessar %URL% >> %LOG%
) else (
    echo Site OK!
)

pause
goto MENU
````

## 🖥️ Como usar

### 1️⃣ Crie um arquivo de texto

Exemplo:
monitor.bat

### 2️⃣ Cole todo o script dentro do arquivo
### 3️⃣ Salve como .bat

No bloco de notas, escolha Salvar como > monitor.bat
Tipo: Todos os arquivos

### 4️⃣ Execute como administrador

Necessário para netstat, net start, net stop.

### 5️⃣ Use o menu do script

Simples, direto e rápido.
