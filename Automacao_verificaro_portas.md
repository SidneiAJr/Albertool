# Automação | Verificador de portas

## Observação em construção:

```bash
#!/bin/bash

BASE_DIR="$(pwd)"
REPORT_DIR="$BASE_DIR/reports"
REPORT_FILE="$REPORT_DIR/relatorio_portas_$(date +%Y%m%d_%H%M%S).txt"

mkdir -p "$REPORT_DIR"

# Portas importantes (DB, web, cache, dev)
PORTAS=(22 80 443 3000 3306 5432 6379 8080)

# ===============================
# Cabeçalho do relatório
# ===============================
cabecalho_relatorio() {
    {
        echo "==========================================="
        echo " Relatório de Portas em Uso"
        echo " Data: $(date)"
        echo " Host: $(hostname)"
        echo "==========================================="
        echo ""
    } >> "$REPORT_FILE"
}

# ===============================
# Verifica processo por porta
# ===============================
verificar_processo_porta() {
    for PORTA in "${PORTAS[@]}"; do
        RESULTADO=$(ss -tulpn 2>/dev/null | grep ":$PORTA ")

        if [ -n "$RESULTADO" ]; then
            echo "🔓 Porta $PORTA EM USO" >> "$REPORT_FILE"
            echo "$RESULTADO" >> "$REPORT_FILE"
            echo "" >> "$REPORT_FILE"
        else
            echo "🔒 Porta $PORTA LIVRE" >> "$REPORT_FILE"
            echo "" >> "$REPORT_FILE"
        fi
    done
}

# ===============================
# Rodar análise
# ===============================
echo "🔎 Verificando portas..."
cabecalho_relatorio
verificar_processo_porta

echo "✅ Relatório gerado em:"
echo "$REPORT_FILE"
```
