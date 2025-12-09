# 📽️Automação | Gravação de Videos & Estrutura:

## 📜Motivo do Script:

## Ajuda quem grava a não perder tempo:

- Cria as pastas
- Cria Documentação
- Logs
- E faz Backup compactado precisa de 7zip

```bash
#!/bin/bash

LOGFILE="script.log"
BACKUP_DIR="bk"

registrar_log() {
    echo "[$(date '+%Y-%m-%d %H:%M:%S')] $1" >> "$LOGFILE"
}

criar_estrutura() {
    echo "Criando estrutura de pastas e arquivos..."
    registrar_log "Criando estrutura de pastas"

    mkdir -p Footage Audio SoundEffects Light Sounds
    mkdir -p Assets/Logo Assets/Overlays Assets/LUTs Assets/Templates
    mkdir -p Project/Adobe Project/DaVinci Project/AfterEffects
    mkdir -p Documentation

    echo "# Checklist de Gravação" > Documentation/checklist_gravacao.md
    echo "# Fluxo de Edição" > Documentation/fluxo_edicao.md
    echo "# Versão do Projeto" > Documentation/versao_projeto.md

    registrar_log "Estrutura criada com sucesso"
    echo "Estrutura criada!"
}

fazer_backup() {
    mkdir -p "$BACKUP_DIR"

    echo "Criando backup..."
    registrar_log "Backup iniciado"

    TIMESTAMP=$(date '+%Y%m%d_%H%M%S')
    BACKUP_FILE="$BACKUP_DIR/backup_$TIMESTAMP.tar.gz"

    tar -czf "$BACKUP_FILE" ./* 2>/dev/null

    registrar_log "Backup criado: $BACKUP_FILE"
    echo "Backup salvo em: $BACKUP_FILE"
}

verificar_tamanhos() {
    echo "Tamanho total do projeto:"
    echo "-----------------------------"
    du -sh . 2>/dev/null
    echo ""
    echo "Top 10 maiores pastas/arquivos:"
    echo "-----------------------------"
    du -ah . 2>/dev/null | sort -hr | head -10

    registrar_log "Verificação de tamanho realizada"
}

mostrar_menu() {
    echo ""
    echo "=============================="
    echo "     MENU DO GERADOR"
    echo "=============================="
    echo "1) Criar Estrutura"
    echo "2) Fazer Backup"
    echo "3) Verificar Tamanhos"
    echo "4) Ver Logs"
    echo "0) Sair"
    echo ""
    read -p "Escolha uma opção: " opcao
}

while true; do
    mostrar_menu

    case $opcao in
        1)
            criar_estrutura
            ;;
        2)
            fazer_backup
            ;;
        3)
            verificar_tamanhos
            ;;
        4)
            echo ""
            echo "==== LOGS ===="
            cat "$LOGFILE"
            echo "=============="
            ;;
        0)
            echo "Saindo..."
            registrar_log "Script encerrado"
            exit
            ;;
        *)
            echo "Opção inválida!"
            ;;
    esac
done

```
