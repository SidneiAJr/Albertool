# 🧪 CheckDosGuri

**CheckDosGuri** é uma automação em **Bash** criada para ajudar desenvolvedores a entender rapidamente a estrutura e as dependências de um projeto.

A ideia é simples: entrar em um projeto, rodar o script e ter um diagnóstico claro do que aquele repositório usa — linguagens, gerenciadores de dependência e ferramentas.

> Projeto simples, direto e feito pra resolver problema real de dev.

---

## 🚀 O que o CheckDosGuri faz

* 🔍 Detecta tecnologias do projeto a partir de arquivos comuns
* 📦 Gera um log com dependências instaladas
* 🧠 Ajuda a entender projetos novos ou legados rapidamente
* 📄 Cria um relatório local sem alterar o projeto

---

## 🛠️ Tecnologias detectadas

O script identifica automaticamente:

* **Node.js** (`package.json`)
* **PHP / Composer** (`composer.json`)
* **Java**

  * Maven (`pom.xml`)
  * Gradle (`build.gradle`)
* **Python** (`requirements.txt`)
* **Docker** (`docker-compose.yml`)
* **Git** (diretório `.git`)
* **Variáveis de ambiente** (`.env.example`)

---

## 📁 Estrutura gerada

Ao rodar o script, será criada a pasta:

```bash
CheckDosGuri/
└── dependencias.log
```

Esse arquivo contém todas as informações detectadas no projeto.

---






## Use o menu interativo:

```text
1 | Checar Arquivos
2 | Gerar Log de Dependências
0 | Sair
```

---

## 📄 Exemplo de saída

```text
✔ Node.js detectado (package.json)
✔ Docker detectado
✔ Repositório Git detectado

[Node.js]
express
dotenv
cors
```

---

## 🎯 Quando usar

* Entrou em um projeto novo e não sabe o stack
* Projeto antigo sem documentação
* Auditoria rápida de dependências
* Padronização de automações locais

---

## 📚 Como Usar
- Crie uma pasta no seu computador.
- Dentro dela, crie um arquivo de texto comum.
- Cole o script completo fornecido no GitHub.
- Salve com a extensão:
- setup.sh
- Clique com botão direito → Executar com Git Bash
- Escolha as opções no menu e deixe a CLI trabalhar sozinha.
---

## ☕ Apoio

Se esse script te ajudou de alguma forma, considere apoiar com um café.
Projeto open source, feito de dev pra dev.

---

## 📜 Licença

Uso livre para fins educacionais e profissionais.
É proibida a venda ou comercialização direta do script.


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
