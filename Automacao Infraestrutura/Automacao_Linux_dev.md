# Automação | Construcao

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

install_pycharm() {
    snap install pycharm-community --classic
}

install_intellij() {
    snap install intellij-idea-community --classic
}

install_netbeans() {
    apt install -y netbeans
}

# ============================
# PROFILES
# ============================

profile_student() {
    update_system
    install_base_tools
    install_python_base
    install_vscode
}

profile_dev_web() {
    update_system
    install_base_tools
    install_php_base
    install_nodejs
    install_mysql_tools
    install_vscode
}

profile_backend() {
    update_system
    install_base_tools
    install_java_base
    install_python_base
    install_postgresql_tools
    install_xampp
    install_docker
    install_intellij
}

profile_security() {
    update_system
    install_base_tools
    install_security_tools
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



