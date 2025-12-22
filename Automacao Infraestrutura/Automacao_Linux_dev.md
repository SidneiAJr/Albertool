# Automação | Debian Dev Installer

Um script Bash para automatizar a instalação de ambientes de desenvolvimento no Debian/Ubuntu.  
Inclui Python, Java, PHP, Node.js, bancos de dados, Docker, ferramentas de segurança e IDEs básicas.

---

## 📌 Funcionalidades

- **Core Tools**: curl, wget, git, unzip, htop, entre outros.
- **Python**: Python 3, pip, venv, Tkinter, Pygame, flake8, pytest.
- **Python Packages**: pandas, numpy, matplotlib, seaborn, requests, fastapi, Flask, SQLAlchemy, entre outros.
- **Java**: OpenJDK 17.
- **PHP**: PHP CLI, extensões MySQL, cURL, XML, Mbstring.
- **Node.js & NPM**: instalação via repositório Debian.
- **Databases**: PostgreSQL, MariaDB.
- **Containers**: Docker + Docker Compose.
- **Security Tools**: nmap, tcpdump, wireshark, net-tools.
- **IDE**: VSCode.
- **Perfis de instalação**: Student, Dev Web, Backend, Security.

---

## 🛠 Perfis de instalação

O script oferece quatro perfis de instalação:

1. **Student**  
   Instala ferramentas básicas, Python e VSCode, além de pacotes Python via pip.

2. **Dev Web**  
   Instala PHP, Node.js, MariaDB, VSCode e ferramentas básicas.

3. **Backend**  
   Instala Java, Python, PostgreSQL, Docker e ferramentas básicas.

4. **Security**  
   Instala apenas ferramentas básicas e de segurança.

---

## 📂 Estrutura do Script
```bash
check_root: garante que o script rode como root.
update_system: atualiza o sistema.
install_base_tools: instala ferramentas essenciais.
install_python_base & install_python_pip_packages: instala Python e pacotes comuns.
install_java_base: instala Java (OpenJDK 17).
install_php_base: instala PHP e extensões.
install_nodejs: instala Node.js e npm.
install_postgresql_tools / install_mariadb: instala bancos de dados.
install_docker: instala Docker e Docker Compose.
install_security_tools: instala ferramentas de rede e segurança.
install_vscode: instala VSCode via repositório oficial da Microsoft.
Perfis (profile_student, profile_dev_web, etc.) combinam os módulos acima.
log_install: registra logs da instalação em /var/log/dev-installer.
```

### 📚 Como Usar
- Crie uma pasta no seu computador.
- Dentro dela, crie um arquivo de texto comum.
- Cole o script completo fornecido no GitHub.
- Salve com a extensão:
- setup.sh
- Clique com botão direito → Executar com Git Bash
- Escolha as opções no menu e deixe a CLI trabalhar sozinha.


## 📝 Observações

Script testado em Linux Mint XFCE recentes.

## Script:

```bash
#!/bin/bash

# ============================
# CORE
# ============================

check_root() {
    if [[ $EUID -ne 0 ]]; then
        echo "Execute como root (sudo)"
        exit 1
    fi
}

update_system() {
    apt update -y && apt upgrade -y
}

install_base_tools() {
    apt install -y \
        curl \
        wget \
        git \
        unzip \
        ca-certificates \
        software-properties-common \
        htop
}

# ============================
# PYTHON
# ============================

install_python_base() {
    apt install -y \
        python3 \
        python3-pip \
        python3-venv \
        python3-tk \
        python3-pygame \
        flake8 \
        pytest
}

install_python_pip_packages() {
    echo "Criando ambiente virtual Python..."

    PY_ENV="/home/$SUDO_USER/.venvs/python"

    mkdir -p "$(dirname "$PY_ENV")"
    python3 -m venv "$PY_ENV"

    "$PY_ENV/bin/python" -m pip install --upgrade pip

    "$PY_ENV/bin/python" -m pip install \
        pandas numpy matplotlib seaborn \
        mysql-connector-python psycopg2-binary \
        black isort mypy \
        requests httpx beautifulsoup4 lxml \
        fastapi uvicorn flask \
        sqlalchemy alembic pydantic python-dotenv \
        typer click rich schedule watchdog \
        paramiko fabric

}


# ============================
# JAVA
# ============================

install_java_base() {
    apt install -y openjdk-17-jdk
}

# ============================
# PHP
# ============================

install_php_base() {
    apt install -y \
        php \
        php-cli \
        php-mysql \
        php-curl \
        php-xml \
        php-mbstring
}

# ============================
# JAVASCRIPT / NODE
# ============================

install_nodejs() {
    apt install -y nodejs npm
}

# ============================
# DATABASES
# ============================

install_xampp() {
    echo "Instalando XAMPP..."

    wget -O /tmp/xampp-installer.run https://www.apachefriends.org/xampp-files/8.2.12/xampp-linux-x64-8.2.12-0-installer.run

    chmod +x /tmp/xampp-installer.run
    sudo /tmp/xampp-installer.run
}

install_postgresql_tools() {
    apt install -y \
        postgresql \
        postgresql-contrib
}

install_mariadb() {
    apt install -y mariadb-server mariadb-client
}

# ============================
# CONTAINERS
# ============================

install_docker() {
    apt install -y docker.io docker-compose
    systemctl enable docker
    systemctl start docker
}

# ============================
# SECURITY
# ============================

install_security_tools() {
    apt install -y \
        nmap \
        tcpdump \
        wireshark \
        net-tools
}

# ============================
# IDEs
# ============================

install_vscode() {
wget -qO- https://packages.microsoft.com/keys/microsoft.asc | gpg --dearmor > microsoft.gpg
sudo install -o root -g root -m 644 microsoft.gpg /etc/apt/trusted.gpg.d/
sudo sh -c 'echo "deb [arch=amd64] https://packages.microsoft.com/repos/code stable main" > /etc/apt/sources.list.d/vscode.list'
sudo apt update
sudo apt install code -y

}

install_snap_if_missing() {
    if ! command -v snap &> /dev/null; then
        echo "Snap não encontrado, instalando..."
        apt update
        apt install -y snapd
        systemctl enable --now snapd.socket
        snap install core
        snap refresh core
    fi
}


install_pycharm() {
    install_snap_if_missing
    snap install pycharm-community --classic
}

install_intellij() {
    install_snap_if_missing
    snap install intellij-idea-community --classic
}


install_netbeans() {
    wget https://downloads.apache.org/netbeans/netbeans/22/Apache-NetBeans-17-bin-linux-x64.sh -O /tmp/netbeans.sh
    chmod +x /tmp/netbeans.sh
    /tmp/netbeans.sh --silent
}


# ============================
# PROFILES
# ============================

profile_student() {
    update_system
    install_base_tools
    install_python_base
    install_vscode
    install_python_pip_packages
    log_install
}

profile_dev_web() {
    update_system
    install_base_tools
    install_php_base
    install_nodejs
    install_mariadb
    install_vscode
    log_install
}

profile_backend() {
    update_system
    install_base_tools
    install_java_base
    install_python_base
    install_postgresql_tools
    install_docker
    install_intellij
    log_install
}

profile_security() {
    update_system
    install_base_tools
    install_security_tools
}

log_install() {
    LOG_DIR="/var/log/dev-installer"
    LOG_FILE="$LOG_DIR/install_$(date +%Y-%m-%d_%H-%M-%S).log"

    mkdir -p "$LOG_DIR"

    echo "====================================" >> "$LOG_FILE"
    echo " Dev Installer Log" >> "$LOG_FILE"
    echo " Data: $(date)" >> "$LOG_FILE"
    echo " Usuário: $SUDO_USER" >> "$LOG_FILE"
    echo " Host: $(hostname)" >> "$LOG_FILE"
    echo " Sistema: $(lsb_release -ds 2>/dev/null || cat /etc/os-release | head -n1)" >> "$LOG_FILE"
    echo "====================================" >> "$LOG_FILE"

    exec > >(tee -a "$LOG_FILE") 2>&1
}


# ============================
# MENUS
# ============================

main_menu() {
    clear
    echo "============================="
    echo " Debian Only - APT Installer"
    echo "============================="
    echo "1 | Student"
    echo "2 | Dev Web"
    echo "3 | Dev Backend"
    echo "4 | Security"
    echo "0 | Exit"
    echo "============================="
    read -p "Escolha uma opção: " option

    case $option in
        1) profile_student ;;
        2) profile_dev_web ;;
        3) profile_backend ;;
        4) profile_security ;;
        0) exit 0 ;;
        *) echo "Opção inválida" ;;
    esac
}

# ============================
# START
# ============================

check_root
main_menu


```


