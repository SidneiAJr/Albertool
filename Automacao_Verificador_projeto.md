# Automação | Checkdosguri



```bash
#!/bin/bash

BASE_DIR="$(pwd)"
LOG_DIR="$BASE_DIR/CheckDosGuri"
LOG_DEPS="$LOG_DIR/dependencias.log"
README="$BASE_DIR/README.md"

# ================================
# BANNER
# ================================
clear
echo "=================================="
echo "  🧪 CheckDosGuri - Project Check "
echo "=================================="

mkdir -p "$LOG_DIR"

# ================================
# FUNÇÕES AUXILIARES
# ================================
comando_existe() {
    command -v "$1" >/dev/null 2>&1
}

log() {
    echo "$1" | tee -a "$LOG_DEPS"
}

# ================================
# CHECK DE ARQUIVOS
# ================================
checar_arquivos() {
    echo ""
    echo "[+] Checando estrutura do projeto..."
    echo "===== CHECK DE ARQUIVOS =====" > "$LOG_DEPS"

    [[ -f package.json ]]        && log "✔ Node.js detectado (package.json)"
    [[ -f composer.json ]]       && log "✔ PHP detectado (composer.json)"
    [[ -f pom.xml ]]             && log "✔ Java detectado (Maven)"
    [[ -f build.gradle ]]        && log "✔ Java detectado (Gradle)"
    [[ -f requirements.txt ]]    && log "✔ Python detectado"
    [[ -f docker-compose.yml ]]  && log "✔ Docker detectado"
    [[ -f .env.example ]]        && log "✔ .env.example encontrado"
    [[ -d .git ]]                && log "✔ Repositório Git detectado"

    echo "[✓] Checagem concluída"
}

# ================================
# LOG DE DEPENDÊNCIAS
# ================================
gerar_log_dependencias() {
    echo ""
    echo "[+] Gerando log de dependências..."

    {
        echo ""
        echo "===== DEPENDÊNCIAS ====="

        if [[ -f package.json ]] && comando_existe npm; then
            echo ""
            echo "[Node.js]"
            npm list --depth=0 2>/dev/null
        fi

        if [[ -f requirements.txt ]]; then
            echo ""
            echo "[Python]"
            cat requirements.txt
        fi

        if [[ -f composer.json ]] && comando_existe composer; then
            echo ""
            echo "[PHP]"
            composer show 2>/dev/null
        fi
    } >> "$LOG_DEPS"

    echo "[✓] Log salvo em: $LOG_DEPS"
}

# ================================
# MENU
# ================================
menu() {
    echo ""
    echo "========= MENU ========="
    echo "1 | Checar Arquivos"
    echo "2 | Gerar Log de Dependências"
    echo "0 | Sair"
    echo "========================"
    read -p "Escolha uma opção: " OPCAO

    case $OPCAO in
        1) checar_arquivos ;;
        2) gerar_log_dependencias ;;
        0) echo "Saindo..."; exit ;;
        *) echo "❌ Opção inválida" ;;
    esac
}

# ================================
# LOOP PRINCIPAL
# ================================
while true; do
    menu
done
```
