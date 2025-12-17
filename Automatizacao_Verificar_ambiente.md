# 🤖 Automatizador | Verificador de Ambiente:

Script em Bash para verificar e gerar relatório do ambiente de desenvolvimento.

## O que ele verifica
- Sistema operacional e arquitetura
- Node.js / NPM
- Java
- .NET SDK
- Python / Pip
- Compiladores C / C++
- Git
- Docker
- MySQL / PostgreSQL

````
#!/bin/bash

BASE_DIR="$(dirname "$(realpath "$0")")"
LOG_FILE="$BASE_DIR/ambiente.log"

echo "===================================================="
echo " Verificador de Ambiente"
echo " Será criado um log na pasta do script"
echo "===================================================="

comando_existe() {
    command -v "$1" >/dev/null 2>&1
}

verificar_versao_npm() {
    if comando_existe npm; then
        echo "NPM: $(npm -v)"
    else
        echo "NPM não instalado"
    fi
}

verificar_versao_java() {
    if comando_existe java; then
        java -version 2>&1 | head -n 1
    else
        echo "Java não instalado"
    fi
}

verificar_versao_cs() {
    if comando_existe dotnet; then
        echo ".NET SDK: $(dotnet --version)"
    else
        echo ".NET SDK não instalado"
    fi
}

verificar_versao_c() {
    if comando_existe gcc; then
        gcc --version | head -n 1
    elif comando_existe clang; then
        clang --version | head -n 1
    else
        echo "Compilador C não encontrado"
    fi
}

verificar_python() {
    if comando_existe python3; then
        echo "Python: $(python3 --version)"
    else
        echo "Python não instalado"
    fi

    if comando_existe pip3; then
        echo "Pip: $(pip3 --version | cut -d' ' -f1,2)"
    else
        echo "Pip não instalado"
    fi
}

criar_relatorio() {
    {
        echo "===== RELATÓRIO DE AMBIENTE ====="
        echo "Data: $(date)"
        echo "--------------------------------"

        echo "[Sistema]"
        uname -a
        echo "--------------------------------"

        echo "[Node]"
        verificar_node
        verificar_versao_npm
        echo "--------------------------------"

        echo "[Java / .NET]"
        verificar_versao_java
        verificar_versao_cs
        echo "--------------------------------"

        echo "[Python]"
        verificar_python
        echo "--------------------------------"

        echo "[Compiladores]"
        verificar_versao_c
        verificar_cpp
        echo "--------------------------------"

        echo "[DevOps]"
        verificar_git
        verificar_docker
        echo "--------------------------------"

        echo "[Banco de Dados]"
        verificar_mysql
        verificar_postgres
    } > "$LOG_FILE"
}


verificar_node() {
    if comando_existe node; then
        echo "Node.js: $(node -v)"
    else
        echo "Node.js não instalado"
    fi
}

verificar_git() {
    if comando_existe git; then
        echo "Git: $(git --version)"
    else
        echo "Git não instalado"
    fi
}
verificar_docker() {
    if comando_existe docker; then
        echo "Docker: $(docker --version)"
    else
        echo "Docker não instalado"
    fi
}
verificar_mysql() {
    if comando_existe mysql; then
        echo "MySQL: $(mysql --version)"
    else
        echo "MySQL não instalado"
    fi
}
verificar_postgres() {
    if comando_existe psql; then
        echo "PostgreSQL: $(psql --version)"
    else
        echo "PostgreSQL não instalado"
    fi
}
verificar_cpp() {
    if comando_existe g++; then
        echo "G++: $(g++ --version | head -n 1)"
    else
        echo "G++ não instalado"
    fi
}


criar_relatorio

echo "Relatório criado em: $LOG_FILE"

````
