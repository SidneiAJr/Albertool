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

## 📦 Requisitos

Para executar corretamente:

- ✔ Git instalado
- ✔ Node.js instalado

## 🙏 Agradecimento
- Obrigado a todos os desenvolvedores que utilizam a Constellation Supreme CLI.
- É simples, porém extremamente funcional e focada em produtividade.
- Se possível, aceitei um café ☕ como forma de apoio — agradeço demais!

## 📚 Como Usar
- Crie uma pasta no seu computador.
- Dentro dela, crie um arquivo de texto comum.
- Cole o script completo fornecido na seção [setup.sh](#setupsh).
- Salve com a extensão:
- setup.sh
- Crie também um arquivo texto comum
- Cole o script completo fornecido no seção [comandos.list](#comandoslist).
- Salve com a extensão:
- comandos.list
- Clique com botão direito → Executar com Git Bash
- Escolha as opções no menu e deixe a CLI trabalhar sozinha.

### setup.sh
````bash
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

verificar_comandos() {
    local lista="$BASE_DIR/comandos.list"

    if [ ! -f "$lista" ]; then
        echo "Arquivo comandos.list não encontrado em $BASE_DIR"
        return
    fi

    while IFS= read -r linha || [ -n "$linha" ]; do
        # Ignora linhas vazias
        [ -z "$linha" ] && continue

        # Separa parte antes e depois de "="
        local nome_label="${linha%%=*}"
        local comando="${linha#*=}"

        # Extrai label entre colchetes, se existir; senão usa o identificador
        local identificador="${nome_label%%[*}"
        local label="${nome_label#*[}"
        if [ "$label" = "$nome_label" ]; then
            label="$identificador"
        else
            label="${label%]}"
        fi

        # Remove espaços extras do comando
        comando="$(echo "$comando" | sed 's/^[[:space:]]*//;s/[[:space:]]*$//')"

        # Pega apenas o binário principal para testar se existe
        local binario="${comando%% *}"
        if [ -z "$binario" ]; then
            echo "$label sem comando configurado"
            continue
        fi

        echo "[$label]"
        if comando_existe "$binario"; then
            local saida
            saida=$($comando 2>&1 | head -n 1)
            echo "$saida"
        else
            echo "$label não instalado"
        fi
        echo "-------------------"
    done < "$lista"
}

criar_relatorio() {
    {
        echo "===== RELATÓRIO DE AMBIENTE ====="
        echo "Data: $(date)"
        echo "--------------------------------"

        echo "[Sistema]"
        uname -a
        echo "--------------------------------"

        verificar_comandos
    } > "$LOG_FILE"
}

criar_relatorio

echo "Relatório criado em: $LOG_FILE"
````

### comandos.list
````bash
NPM[NPM]=npm -v
JAVA[Java]=java -version
DOTNET[.NET SDK]=dotnet --version
GCC[Compilador C GCC]=gcc --version
GPP[Compilador C GPP]=g++ --version
CLANG=clang --version
PYTHON[Python]=python3 --version
PIP[PIP]=pip3 --version
NODE[Node.js]=node -v
GIT[GIT]=git --version
DOCKER[Docker]=docker --version
MYSQL[MySQL]=mysql --version
POSTGRES[PostgreSQL]=psql --version
````
