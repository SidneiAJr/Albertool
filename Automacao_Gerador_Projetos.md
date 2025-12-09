# 📜Automação | Gerador de Projetos 

## `Linguagens Suportadas`:

<p align="center">
<img src="https://cdn.jsdelivr.net/gh/devicons/devicon@latest/icons/python/python-original-wordmark.svg" height=50px width =50px />
<img src="https://cdn.jsdelivr.net/gh/devicons/devicon@latest/icons/csharp/csharp-original.svg" height=50px width =50px />
<img src="https://cdn.jsdelivr.net/gh/devicons/devicon@latest/icons/java/java-original-wordmark.svg" height=50px width =50px />
<img src="https://cdn.jsdelivr.net/gh/devicons/devicon@latest/icons/cplusplus/cplusplus-original.svg" height=50px width =50px />  
</p>

## ⚒️Albertool 

## Função:

- Criar Projetos em C# C+ Java PY
- Importa as libs necessarias em PY e Java
- Cria a pasta
- Pergunta o Nome do projeto
- Gera POO para C# e Java

## `Versão Alpha | Cria so o Basico| Alpha Version | Fix Bugs`

````bash
#!/bin/bash

clear
echo "=========================================="
echo "   🚀 GERADOR AUTOMÁTICO DE PROJETOS"
echo "=========================================="
echo ""

read -p "Nome do projeto: " PROJ
mkdir -p "$PROJ"
cd "$PROJ"

# ========================================================
# MENU PRINCIPAL — ESCOLHA DA LINGUAGEM
# ========================================================
echo ""
echo "Selecione a linguagem:"
echo "1) Python"
echo "2) Java"
echo "3) C#"
echo "4) C++"
echo ""

read -p "Opção: " LANG


# ========================================================
# FUNÇÃO — GERA IMPORTS AUTOMATICAMENTE
# ========================================================
gerar_imports_python() {
    IFS=',' read -ra LIBS <<< "$1"

    echo "import sys" >> src/main.py

    for lib in "${LIBS[@]}"; do
        lib=$(echo "$lib" | xargs) # trim
        echo "import $lib" >> src/main.py
        echo "$lib" >> requirements.txt
    done
}

gerar_imports_java() {
    IFS=',' read -ra LIBS <<< "$1"

cat <<EOF >> src/Main.java
package app;

public class Main {
    public static void main(String[] args) {

EOF

    for lib in "${LIBS[@]}"; do
        lib=$(echo "$lib" | xargs)

        case $lib in
            json)
                echo "import org.json.JSONObject;" > imports.tmp
                ;;
            jdbc)
                echo "import java.sql.*;" > imports.tmp
                ;;
            *)
                echo "// Lib '$lib' não reconhecida, inclua manualmente" > imports.tmp
                ;;
        esac

        cat imports.tmp | cat - src/Main.java > temp && mv temp src/Main.java
        echo "    // usando $lib" >> src/Main.java
    done

cat <<EOF >> src/Main.java
    }
}
EOF
}

gerar_imports_cs() {
    IFS=',' read -ra LIBS <<< "$1"

cat <<EOF >> Program.cs
using System;

EOF

    for lib in "${LIBS[@]}"; do
        lib=$(echo "$lib" | xargs)

        case $lib in
            http)
                echo "using System.Net.Http;" >> Program.cs;;
            json)
                echo "using Newtonsoft.Json;" >> Program.cs;;
            *)
                echo "// lib '$lib' não reconhecida" >> Program.cs;;
        esac
    done

cat <<EOF >> Program.cs
class Program {
    static void Main() {
        Console.WriteLine("Projeto $PROJ iniciado!");
    }
}
EOF
}

gerar_imports_cpp() {
    IFS=',' read -ra LIBS <<< "$1"

cat <<EOF >> src/main.cpp
#include <iostream>
EOF

    for lib in "${LIBS[@]}"; do
        lib=$(echo "$lib" | xargs)

        case $lib in
            sdl)
                echo "#include <SDL2/SDL.h>" >> src/main.cpp;;
            opengl)
                echo "#include <GL/glew.h>" >> src/main.cpp
                echo "#include <GLFW/glfw3.h>" >> src/main.cpp;;
            *)
                echo "// Lib '$lib' desconhecida" >> src/main.cpp;;
        esac
    done

cat <<EOF >> src/main.cpp

int main() {
    std::cout << "Projeto $PROJ iniciado!" << std::endl;
    return 0;
}
EOF
}

# ========================================================
# PYTHON
# ========================================================
if [ "$LANG" == "1" ]; then

    mkdir -p src
    touch src/main.py
    touch requirements.txt

    echo "print('Projeto $PROJ iniciado')" > src/main.py

    read -p "Adicionar bibliotecas? (ex: pygame, requests, numpy): " LIBS
    gerar_imports_python "$LIBS"

    echo "VIRTUALENV e dependências prontos!"
fi


# ========================================================
# JAVA
# ========================================================
if [ "$LANG" == "2" ]; then
    mkdir -p src
    mkdir -p lib

    touch pom.xml
    touch src/Main.java

    read -p "Adicionar libs? (ex: json, jdbc): " LIBS
    gerar_imports_java "$LIBS"

cat <<EOF > pom.xml
<project>
  <modelVersion>4.0.0</modelVersion>
  <groupId>app</groupId>
  <artifactId>$PROJ</artifactId>
  <version>1.0</version>
</project>
EOF

fi


# ========================================================
# C#
# ========================================================
if [ "$LANG" == "3" ]; then
    touch Program.cs
    touch "$PROJ.csproj"

cat <<EOF > "$PROJ.csproj"
<Project Sdk="Microsoft.NET.Sdk">
  <PropertyGroup>
    <OutputType>Exe</OutputType>
    <TargetFramework>net8.0</TargetFramework>
  </PropertyGroup>
</Project>
EOF

    read -p "Adicionar libs? (ex: http, json): " LIBS
    gerar_imports_cs "$LIBS"
fi


# ========================================================
# C++
# ========================================================
if [ "$LANG" == "4" ]; then
    mkdir -p src
    touch src/main.cpp
    touch CMakeLists.txt

    read -p "Adicionar libs? (ex: sdl, opengl): " LIBS
    gerar_imports_cpp "$LIBS"

cat <<EOF > CMakeLists.txt
cmake_minimum_required(VERSION 3.10)
project($PROJ)
set(CMAKE_CXX_STANDARD 17)
add_executable($PROJ src/main.cpp)
EOF
fi


echo ""
echo "=========================================="
echo "   ✔ PROJETO $PROJ GERADO COM SUCESSO!"
echo "=========================================="
````


## `New Version | Beta version | Create POO Struture`

- Cria os projetos
- Opção de criar O projeto em POO com uma Interface + 3 classes + com variaveis

````bash
#!/bin/bash

clear
clear
cat << "EOF"
   █████╗ ██╗     ██████╗ ███████╗██████╗ ████████╗ ██████╗  ██████╗ ██╗     
  ██╔══██╗██║     ██╔══██╗██╔════╝██╔══██╗╚══██╔══╝██╔═══██╗██╔═══██╗██║     
  ███████║██║     ██║  ██║█████╗  ██████╔╝   ██║   ██║   ██║██║   ██║██║     
  ██╔══██║██║     ██║  ██║██╔══╝  ██╔══██╗   ██║   ██║   ██║██║   ██║██║     
  ██║  ██║███████╗██████╔╝███████╗██║  ██║   ██║   ╚██████╔╝╚██████╔╝███████╗
  ╚═╝  ╚═╝╚══════╝╚═════╝ ╚══════╝╚═╝  ╚═╝   ╚═╝    ╚═════╝  ╚═════╝ ╚══════╝
                        PROJECT GENERATOR
EOF


read -p "Nome do projeto: " PROJ
mkdir -p "$PROJ"
cd "$PROJ"

# ========================================================
#        FUNÇÃO AUXILIAR
# ========================================================
pause() {
    read -p "Pressione ENTER para continuar..."
}

# ========================================================
#        FUNÇÃO — GERAR POO (JAVA E C#) aceita parâmetro
#        Usage: gerar_poo 2   # 2 = Java
#               gerar_poo 3   # 3 = C#
# ========================================================
gerar_poo() {
    local lang="$1"

    if [ "$lang" == "2" ]; then
        echo "Gerando estrutura POO em Java..."
        mkdir -p src/app/core

cat <<EOF > src/app/core/IAction.java
package app.core;

public interface IAction {
    void executar();
}
EOF

cat <<EOF > src/app/core/BaseAction.java
package app.core;

public abstract class BaseAction implements IAction {

    protected String name;

    public BaseAction(String name) {
        this.name = name;
    }

    public void info() {
        System.out.println("Executando ação: " + name);
    }
}
EOF

cat <<EOF > src/app/core/LoginAction.java
package app.core;

public class LoginAction extends BaseAction {

    public LoginAction() {
        super("Login");
    }

    @Override
    public void executar() {
        info();
        System.out.println("Efetuando login...");
    }
}
EOF

cat <<EOF > src/app/core/LogoutAction.java
package app.core;

public class LogoutAction extends BaseAction {

    public LogoutAction() {
        super("Logout");
    }

    @Override
    public void executar() {
        info();
        System.out.println("Efetuando logout...");
    }
}
EOF

cat <<EOF > src/Main.java
package app;

import app.core.*;

public class Main {
    public static void main(String[] args) {

        IAction login = new LoginAction();
        IAction logout = new LogoutAction();

        login.executar();
        logout.executar();
    }
}
EOF

        echo "✔ Estrutura POO Java gerada!"

    elif [ "$lang" == "3" ]; then
        echo "Gerando estrutura POO em C#..."
        mkdir -p Core

cat <<EOF > Core/IAction.cs
namespace Core {
    public interface IAction {
        void Executar();
    }
}
EOF

cat <<EOF > Core/BaseAction.cs
using System;

namespace Core {

    public abstract class BaseAction : IAction {

        protected string Name;

        public BaseAction(string name) {
            Name = name;
        }

        public virtual void Info() {
            Console.WriteLine($"Executando ação: {Name}");
        }

        public abstract void Executar();
    }
}
EOF

cat <<EOF > Core/LoginAction.cs
using System;

namespace Core {

    public class LoginAction : BaseAction {

        public LoginAction() : base("Login") {}

        public override void Executar() {
            Info();
            Console.WriteLine("Efetuando login...");
        }
    }
}
EOF

cat <<EOF > Core/LogoutAction.cs
using System;

namespace Core {

    public class LogoutAction : BaseAction {

        public LogoutAction() : base("Logout") {}

        public override void Executar() {
            Info();
            Console.WriteLine("Efetuando logout...");
        }
    }
}
EOF

cat <<EOF > Program.cs
using Core;
using System;

class Program {
    static void Main() {

        IAction login = new LoginAction();
        IAction logout = new LogoutAction();

        login.Executar();
        logout.Executar();
    }
}
EOF

        echo "✔ Estrutura POO C# gerada!"

    else
        echo "❌ Estrutura POO só aceita '2' (Java) ou '3' (C#). Nada gerado."
    fi
}

# ========================================================
#        MENU PYTHON 
# ========================================================
menu_python() {
    clear
    echo "=========================================="
    echo "     🐍 ESCOLHA O TIPO DE PROJETO PYTHON"
    echo "=========================================="
    echo "1) Projeto básico"
    echo "2) Pygame"
    echo "3) Tkinter"
    echo "4) FastAPI"
    echo "5) Pandas"
    echo "6) Python + SQL (CRUD automático)"
    echo "=========================================="
    read -p "Opção: " OP

    mkdir -p src
    touch src/main.py
    touch requirements.txt

    case $OP in
        1)
            echo "print('Projeto $PROJ iniciado!')" > src/main.py
            ;;
        2)
            cat > src/main.py <<PY
import pygame

pygame.init()
screen = pygame.display.set_mode((800,600))
pygame.display.set_caption('$PROJ')

running = True
while running:
    for event in pygame.event.get():
        if event.type == pygame.QUIT:
            running = False

pygame.quit()
PY
            echo "pygame" >> requirements.txt
            ;;
        3)
            cat > src/main.py <<PY
import tkinter as tk

root = tk.Tk()
root.title('$PROJ')
root.geometry('400x300')
tk.Label(root, text='Projeto $PROJ iniciado').pack()
root.mainloop()
PY
            echo "tkinter" >> requirements.txt
            ;;
        4)
            cat > src/main.py <<PY
from fastapi import FastAPI

app = FastAPI()

@app.get('/')
def index():
    return {'Projeto': '$PROJ'}
PY
            echo "fastapi" >> requirements.txt
            echo "uvicorn" >> requirements.txt
            ;;
        5)
            cat > src/main.py <<PY
import pandas as pd

df = pd.DataFrame({'Projeto': ['$PROJ'], 'Status': ['Iniciado']})
print(df)
PY
            echo "pandas" >> requirements.txt
            ;;
        6)
            cat > src/main.py <<PY
import sqlite3

conn = sqlite3.connect('database.db')
cur = conn.cursor()

cur.execute("CREATE TABLE IF NOT EXISTS users (id INTEGER PRIMARY KEY, nome TEXT)")

def inserir(nome):
    cur.execute('INSERT INTO users (nome) VALUES (?)', (nome,))
    conn.commit()

def listar():
    cur.execute('SELECT * FROM users')
    return cur.fetchall()

inserir('Usuario Teste')
print(listar())
PY
            echo "sqlite3" >> requirements.txt
            ;;
        *)
            echo "Opção inválida."
            ;;
    esac
}

# ========================================================
#        MENU PRINCIPAL — ESCOLHA A LINGUAGEM
# ========================================================
echo ""
echo "Selecione a linguagem:"
echo "1) Python"
echo "2) Java"
echo "3) C#"
echo "4) C++"
echo "5) Gerar estrutura POO (Java / C#)"
echo ""

read -p "Opção: " LANG


# ========================================================
# EXECUÇÃO POR LINGUAGEM
# ========================================================
case "$LANG" in

    1) menu_python;;
    2)
        mkdir -p src
cat <<EOF > src/Main.java
public class Main {
    public static void main(String[] args) {
        System.out.println("Projeto $PROJ iniciado!");
    }
}
EOF
        ;;
    3)
cat <<EOF > Program.cs
using System;

class Program {
    static void Main() {
        Console.WriteLine("Projeto $PROJ iniciado!");
    }
}
EOF
        ;;
    4)
        mkdir -p src
cat <<EOF > src/main.cpp
#include <iostream>

int main() {
    std::cout << "Projeto $PROJ iniciado!" << std::endl;
    return 0;
}
EOF
        ;;
    5)
        echo ""
        echo "Escolha a linguagem para gerar a estrutura POO:"
        echo "2) Java"
        echo "3) C#"
        read -p "Digite 2 ou 3: " POO_LANG
        gerar_poo "$POO_LANG"
        ;;
    *)
        echo "Opção inválida."
        ;;
esac

echo ""
echo "=========================================="
echo "   ✔ PROJETO $PROJ GERADO COM SUCESSO!"
echo "=========================================="

````
