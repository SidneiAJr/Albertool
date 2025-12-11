# 🎲Automação | Gerador de SQL

`Este repositório contém um Gerador de SQL que cria automaticamente bancos de dados e suas respectivas tabelas. O objetivo é fornecer scripts SQL prontos para uso em diferentes cenários, como sistemas de saúde, bibliotecas, hotelaria, e outros. Você pode usar esses scripts para criar bancos de dados com tabelas prontas para inserção de dados, relacionamentos e testes.`

## Tabelas Criadas:
### 1. Banco de Dados: Teste (Test Database)
- Descrição: Banco de dados simples para fins de testes.
- Tabelas Criadas:
- teste1: Armazena informações genéricas como name, city, country, e info.

### 2. Banco de Dados: Company (Empresa)
- Descrição: Banco de dados de exemplo para um sistema de gerenciamento de usuários, login e setores de uma empresa.
- Tabelas Criadas:
- user: Armazena informações dos usuários da empresa, incluindo dados de contato e informações de login.
- login: Armazena informações de login, como email e password.
- setor: Armazena informações sobre os setores da empresa, como o nome e a descrição.

### 3. Banco de Dados: Ecommerce (Comércio Eletrônico)
- Descrição: Banco de dados para um sistema de e-commerce, com informações de produtos, clientes, pedidos e pagamentos.
- Tabelas Criadas:
- products: Armazena informações sobre os produtos, como name, description, price e stock.
- customers: Armazena informações sobre os clientes, como name, email, phone e address.
- orders: Armazena informações sobre os pedidos feitos pelos clientes, incluindo customer_id, order_date, e total_price.
- payments: Armazena informações sobre os pagamentos feitos pelos clientes, incluindo payment_date, amount, e status.

### 4. Banco de Dados: Escola (School)
- Descrição: Banco de dados para um sistema de gerenciamento escolar, incluindo alunos, professores, disciplinas e notas.
- Tabelas Criadas:
- students: Armazena informações sobre os alunos, como name, email, e dob (data de nascimento).
- teachers: Armazena informações sobre os professores, incluindo name, email e subject.
- subjects: Armazena informações sobre as disciplinas oferecidas pela escola, incluindo name e teacher_id.
- grades: Armazena as notas dos alunos nas disciplinas, com referência a student_id e subject_id.

### 5. Banco de Dados: Sistema de Saúde (Health System)
- Descrição: Banco de dados para um sistema de gestão de saúde, incluindo pacientes, médicos, consultas, diagnósticos e prescrições.
- Tabelas Criadas:
- patients: Armazena informações sobre os pacientes, como name, dob, gender, e contact_info.
- doctors: Armazena informações sobre os médicos, como name, specialty, e contact_info.
- appointments: Armazena informações sobre as consultas, com referências a patient_id e doctor_id.
- diagnoses: Armazena os diagnósticos realizados para os pacientes, incluindo patient_id e diagnosis_description.
- prescriptions: Armazena as prescrições médicas, com referência a appointment_id e informações sobre os medicamentos.

### 6. Banco de Dados: Hotelaria (Hospitality)
- Descrição: Banco de dados para um sistema de gerenciamento de hotelaria, com informações sobre quartos, reservas, hóspedes e serviços do hotel.
- Tabelas Criadas:
- rooms: Armazena informações sobre os quartos do hotel, como room_number, room_type, price_per_night e status.
- guests: Armazena informações sobre os hóspedes, como name, email, phone e address.
- reservations: Armazena informações sobre as reservas feitas pelos hóspedes, com referência a guest_id e room_id.
- services: Armazena informações sobre os serviços oferecidos pelo hotel, como service_name e price.
- billing: Armazena informações de cobrança, incluindo os serviços consumidos durante a estadia e o valor total.

### 📚 Como Usar
- Crie uma pasta no seu computador.
- Dentro dela, crie um arquivo de texto comum.
- Cole o script completo fornecido no GitHub.
- Salve com a extensão:
- setup.sh
- Clique com botão direito → Executar com Git Bash
- Escolha as opções no menu e deixe a CLI trabalhar sozinha.

### Script:
````bash
echo ===============================
echo Welcome | DataBase Generator
echo ===============================

# Variáveis
BASE_DIR="./database_scripts"  # Definindo onde os scripts serão salvos
mkdir -p "$BASE_DIR"

menu(){
    echo "Escolha uma opção para gerar o banco de dados:"
    echo "1 - Database | Teste Básico | Uma Tabela"
    echo "2 - Database | Empresa | Registro + Login + Setor"
    echo "3 - Database | Ecommerce | Completo"
    echo "4 - Database | Escola | Completo"
    echo "5 - Database | RH | Completo"
    echo "6 - Database | Hospital | Completo"
    echo "7 - Database | Library | Completo"
    read -p "Digite o número da opção: " option
    case $option in
        1) create_banco_test ;;
        2) create_data_base_company ;;
        3) create_ecommerce_db ;;
        4) create_school_db ;;
        5) create_hr_system_db ;;
        6) create_database_hospital;;
        7) create_database_library ;;
        *) echo "Opção inválida. Tente novamente." ; menu ;;
    esac
}


# Função para criar o banco de dados de teste
create_banco_test(){
    cat <<EOF > "$BASE_DIR/database.sql"
    CREATE DATABASE IF NOT EXISTS teste;
    USE teste;
    CREATE TABLE IF NOT EXISTS teste1 (
        id INT NOT NULL PRIMARY KEY AUTO_INCREMENT,
        name VARCHAR(100) NOT NULL,
        city VARCHAR(100) NOT NULL,
        country VARCHAR(100) NOT NULL,
        info TEXT NOT NULL
    );
    -- Inserir dados mock
    INSERT INTO teste1 (name, city, country, info) VALUES
        ('Alice', 'São Paulo', 'Brasil', 'Informações da Alice'),
        ('Bob', 'Rio de Janeiro', 'Brasil', 'Informações do Bob'),
        ('Carlos', 'Curitiba', 'Brasil', 'Informações do Carlos');
EOF
}

# Função para criar o banco de dados da empresa
create_data_base_company(){
    cat <<EOF > "$BASE_DIR/database.sql"
    -- Table for Register
    CREATE DATABASE IF NOT EXISTS company;
    USE company;
    CREATE TABLE IF NOT EXISTS user (
        id_register INT NOT NULL PRIMARY KEY AUTO_INCREMENT,
        name VARCHAR(100) NOT NULL,
        city VARCHAR(100) NOT NULL,
        country VARCHAR(100) NOT NULL,
        info TEXT NOT NULL,
        password VARCHAR(255) NOT NULL,
        email VARCHAR(255) NOT NULL
    );

    -- Table for Login
    CREATE TABLE IF NOT EXISTS login (
        id_login INT NOT NULL PRIMARY KEY AUTO_INCREMENT,
        password VARCHAR(255) NOT NULL,
        email VARCHAR(255) NOT NULL
    );

    -- Table for Setor
    CREATE TABLE IF NOT EXISTS setor (
        id_setor INT NOT NULL PRIMARY KEY AUTO_INCREMENT,
        setor_name VARCHAR(100) NOT NULL,
        description_setor VARCHAR(100) NOT NULL
    );
    -- Inserir dados mock para usuários
    INSERT INTO user (name, city, country, info, password, email) VALUES
        ('Maria', 'São Paulo', 'Brasil', 'Informações da Maria', 'senha123', 'maria@example.com'),
        ('João', 'Salvador', 'Brasil', 'Informações do João', 'senha456', 'joao@example.com'),
        ('Fernanda', 'Belo Horizonte', 'Brasil', 'Informações da Fernanda', 'senha789', 'fernanda@example.com');

    -- Table for Login
    CREATE TABLE IF NOT EXISTS login (
        id_login INT NOT NULL PRIMARY KEY AUTO_INCREMENT,
        password VARCHAR(255) NOT NULL,
        email VARCHAR(255) NOT NULL
    );

    -- Inserir dados mock para login
    INSERT INTO login (password, email) VALUES
        ('senha123', 'maria@example.com'),
        ('senha456', 'joao@example.com'),
        ('senha789', 'fernanda@example.com');

    -- Table for Setor
    CREATE TABLE IF NOT EXISTS setor (
        id_setor INT NOT NULL PRIMARY KEY AUTO_INCREMENT,
        setor_name VARCHAR(100) NOT NULL,
        description_setor VARCHAR(100) NOT NULL
    );

    -- Inserir dados mock para setores
    INSERT INTO setor (setor_name, description_setor) VALUES
        ('TI', 'Tecnologia da Informação'),
        ('RH', 'Recursos Humanos'),
        ('Financeiro', 'Gestão financeira');
EOF
}

create_ecommerce_db(){
    cat <<EOF > "$BASE_DIR/database.sql"
    CREATE DATABASE IF NOT EXISTS ecommerce;
    USE ecommerce;

    CREATE TABLE IF NOT EXISTS products (
        id INT NOT NULL PRIMARY KEY AUTO_INCREMENT,
        name VARCHAR(100) NOT NULL,
        description TEXT NOT NULL,
        price DECIMAL(10, 2) NOT NULL,
        stock INT NOT NULL
    );

    INSERT INTO products (name, description, price, stock) VALUES
        ('Produto A', 'Descrição do Produto A', 99.90, 10),
        ('Produto B', 'Descrição do Produto B', 49.90, 25),
        ('Produto C', 'Descrição do Produto C', 149.90, 5);

    CREATE TABLE IF NOT EXISTS customers (
        id INT NOT NULL PRIMARY KEY AUTO_INCREMENT,
        name VARCHAR(100) NOT NULL,
        email VARCHAR(100) NOT NULL,
        phone VARCHAR(20) NOT NULL,
        address TEXT NOT NULL
    );

    INSERT INTO customers (name, email, phone, address) VALUES
        ('Cliente 1', 'cliente1@example.com', '123456789', 'Rua A, 123'),
        ('Cliente 2', 'cliente2@example.com', '987654321', 'Rua B, 456');

    CREATE TABLE IF NOT EXISTS orders (
        id INT NOT NULL PRIMARY KEY AUTO_INCREMENT,
        customer_id INT NOT NULL,
        order_date TIMESTAMP DEFAULT CURRENT_TIMESTAMP,
        total_price DECIMAL(10, 2) NOT NULL,
        FOREIGN KEY (customer_id) REFERENCES customers(id)
    );

    CREATE TABLE IF NOT EXISTS payments (
        id INT NOT NULL PRIMARY KEY AUTO_INCREMENT,
        order_id INT NOT NULL,
        payment_date TIMESTAMP DEFAULT CURRENT_TIMESTAMP,
        amount DECIMAL(10, 2) NOT NULL,
        status ENUM('pending', 'paid', 'failed') NOT NULL,
        FOREIGN KEY (order_id) REFERENCES orders(id)
    );
EOF
}


create_school_db(){
    cat <<EOF > "$BASE_DIR/database.sql"
    CREATE DATABASE IF NOT EXISTS school;
    USE school;

    CREATE TABLE IF NOT EXISTS students (
        id INT NOT NULL PRIMARY KEY AUTO_INCREMENT,
        name VARCHAR(100) NOT NULL,
        email VARCHAR(100) NOT NULL,
        dob DATE NOT NULL
    );

    INSERT INTO students (name, email, dob) VALUES
        ('Ana', 'ana@example.com', '2005-04-15'),
        ('Carlos', 'carlos@example.com', '2006-07-22');

    CREATE TABLE IF NOT EXISTS teachers (
        id INT NOT NULL PRIMARY KEY AUTO_INCREMENT,
        name VARCHAR(100) NOT NULL,
        email VARCHAR(100) NOT NULL,
        subject VARCHAR(100) NOT NULL
    );

    INSERT INTO teachers (name, email, subject) VALUES
        ('Professor João', 'joao@example.com', 'Matemática'),
        ('Professor Maria', 'maria@example.com', 'História');

    CREATE TABLE IF NOT EXISTS subjects (
        id INT NOT NULL PRIMARY KEY AUTO_INCREMENT,
        name VARCHAR(100) NOT NULL,
        teacher_id INT NOT NULL,
        FOREIGN KEY (teacher_id) REFERENCES teachers(id)
    );

    INSERT INTO subjects (name, teacher_id) VALUES
        ('Matemática', 1),
        ('História', 2);

    CREATE TABLE IF NOT EXISTS grades (
        id INT NOT NULL PRIMARY KEY AUTO_INCREMENT,
        student_id INT NOT NULL,
        subject_id INT NOT NULL,
        grade DECIMAL(5,2) NOT NULL,
        FOREIGN KEY (student_id) REFERENCES students(id),
        FOREIGN KEY (subject_id) REFERENCES subjects(id)
    );

    INSERT INTO grades (student_id, subject_id, grade) VALUES
        (1, 1, 8.5),
        (1, 2, 9.0),
        (2, 1, 7.0);
EOF
}
create_hr_system_db(){
    cat <<EOF > "$BASE_DIR/database.sql"
    CREATE DATABASE IF NOT EXISTS hr_system;
    USE hr_system;

    CREATE TABLE IF NOT EXISTS employees (
        id INT NOT NULL PRIMARY KEY AUTO_INCREMENT,
        name VARCHAR(100) NOT NULL,
        email VARCHAR(100) NOT NULL,
        position VARCHAR(100) NOT NULL,
        department_id INT NOT NULL,
        salary DECIMAL(10, 2) NOT NULL
    );

    INSERT INTO employees (name, email, position, department_id, salary) VALUES
        ('Marcos', 'marcos@example.com', 'Desenvolvedor', 1, 4500.00),
        ('Júlia', 'julia@example.com', 'Gerente', 2, 8000.00);

    CREATE TABLE IF NOT EXISTS departments (
        id INT NOT NULL PRIMARY KEY AUTO_INCREMENT,
        name VARCHAR(100) NOT NULL
    );

    INSERT INTO departments (name) VALUES
        ('TI'),
        ('Recursos Humanos');

    CREATE TABLE IF NOT EXISTS salaries (
        id INT NOT NULL PRIMARY KEY AUTO_INCREMENT,
        employee_id INT NOT NULL,
        salary DECIMAL(10, 2) NOT NULL,
        date TIMESTAMP DEFAULT CURRENT_TIMESTAMP,
        FOREIGN KEY (employee_id) REFERENCES employees(id)
    );

    INSERT INTO salaries (employee_id, salary) VALUES
        (1, 4500.00),
        (2, 8000.00);
EOF
}

create_database_hospital(){
    cat <<EOF > "$BASE_DIR/database.sql"
    create database hospital;
    use hospital;
    CREATE TABLE IF NOT EXISTS patients (
    id INT NOT NULL PRIMARY KEY AUTO_INCREMENT,
    name VARCHAR(100) NOT NULL,
    dob DATE NOT NULL,
    gender ENUM('M', 'F') NOT NULL,
    contact_info TEXT NOT NULL
);
CREATE TABLE IF NOT EXISTS doctors (
    id INT NOT NULL PRIMARY KEY AUTO_INCREMENT,
    name VARCHAR(100) NOT NULL,
    specialty VARCHAR(100) NOT NULL,
    contact_info TEXT NOT NULL
);
CREATE TABLE IF NOT EXISTS appointments (
    id INT NOT NULL PRIMARY KEY AUTO_INCREMENT,
    patient_id INT NOT NULL,
    doctor_id INT NOT NULL,
    appointment_date TIMESTAMP DEFAULT CURRENT_TIMESTAMP,
    status ENUM('scheduled', 'completed', 'cancelled') NOT NULL,
    FOREIGN KEY (patient_id) REFERENCES patients(id),
    FOREIGN KEY (doctor_id) REFERENCES doctors(id)
);
CREATE TABLE IF NOT EXISTS diagnoses (
    id INT NOT NULL PRIMARY KEY AUTO_INCREMENT,
    patient_id INT NOT NULL,
    diagnosis_date TIMESTAMP DEFAULT CURRENT_TIMESTAMP,
    diagnosis_description TEXT NOT NULL,
    FOREIGN KEY (patient_id) REFERENCES patients(id)
);
CREATE TABLE IF NOT EXISTS prescriptions (
    id INT NOT NULL PRIMARY KEY AUTO_INCREMENT,
    appointment_id INT NOT NULL,
    medicine_name VARCHAR(100) NOT NULL,
    dosage VARCHAR(50) NOT NULL,
    duration VARCHAR(50) NOT NULL,
    FOREIGN KEY (appointment_id) REFERENCES appointments(id)
);
CREATE TABLE IF NOT EXISTS medications (
    id INT NOT NULL PRIMARY KEY AUTO_INCREMENT,
    name VARCHAR(100) NOT NULL,
    description TEXT NOT NULL
);
INSERT INTO patients (name, dob, gender, contact_info) VALUES
    ('Alice Souza', '1990-04-15', 'F', 'alice@example.com'),
    ('José Santos', '1985-07-20', 'M', 'jose@example.com');

INSERT INTO doctors (name, specialty, contact_info) VALUES
    ('Dr. João Silva', 'Cardiologista', 'joao.silva@clinic.com'),
    ('Dra. Maria Oliveira', 'Pediatra', 'maria.oliveira@clinic.com');

INSERT INTO appointments (patient_id, doctor_id, appointment_date, status) VALUES
    (1, 1, '2025-12-15 10:00:00', 'scheduled'),
    (2, 2, '2025-12-16 09:00:00', 'scheduled');

INSERT INTO diagnoses (patient_id, diagnosis_date, diagnosis_description) VALUES
    (1, '2025-12-15', 'Hipertensão arterial'),
    (2, '2025-12-16', 'Resfriado comum');
EOF
}

create_database_library(){
   cat <<EOF > "$BASE_DIR/database.sql"
   create database library;
   use library;
   CREATE TABLE IF NOT EXISTS books (
    id INT NOT NULL PRIMARY KEY AUTO_INCREMENT,
    title VARCHAR(255) NOT NULL,
    author_id INT NOT NULL,
    category_id INT NOT NULL,
    publish_date DATE NOT NULL,
    quantity INT NOT NULL,
    FOREIGN KEY (author_id) REFERENCES authors(id),
    FOREIGN KEY (category_id) REFERENCES categories(id)
);
CREATE TABLE IF NOT EXISTS authors (
    id INT NOT NULL PRIMARY KEY AUTO_INCREMENT,
    name VARCHAR(255) NOT NULL,
    bio TEXT
);
CREATE TABLE IF NOT EXISTS categories (
    id INT NOT NULL PRIMARY KEY AUTO_INCREMENT,
    category_name VARCHAR(100) NOT NULL
);
CREATE TABLE IF NOT EXISTS members (
    id INT NOT NULL PRIMARY KEY AUTO_INCREMENT,
    name VARCHAR(255) NOT NULL,
    email VARCHAR(255) NOT NULL,
    phone VARCHAR(20),
    address TEXT
);
CREATE TABLE IF NOT EXISTS loans (
    id INT NOT NULL PRIMARY KEY AUTO_INCREMENT,
    book_id INT NOT NULL,
    member_id INT NOT NULL,
    loan_date TIMESTAMP DEFAULT CURRENT_TIMESTAMP,
    return_date TIMESTAMP,
    status ENUM('borrowed', 'returned') NOT NULL,
    FOREIGN KEY (book_id) REFERENCES books(id),
    FOREIGN KEY (member_id) REFERENCES members(id)
);
INSERT INTO authors (name, bio) VALUES
    ('J.K. Rowling', 'Autora britânica, famosa por Harry Potter.'),
    ('George Orwell', 'Autor britânico, famoso por 1984.');

INSERT INTO categories (category_name) VALUES
    ('Ficção'),
    ('Não-ficção');

INSERT INTO books (title, author_id, category_id, publish_date, quantity) VALUES
    ('Harry Potter e a Pedra Filosofal', 1, 1, '1997-06-26', 5),
    ('1984', 2, 1, '1949-06-08', 3);

INSERT INTO members (name, email, phone, address) VALUES
    ('Carlos Souza', 'carlos@example.com', '1234567890', 'Rua A, 123'),
    ('Ana Pereira', 'ana@example.com', '0987654321', 'Rua B, 456');

INSERT INTO loans (book_id, member_id, loan_date, return_date, status) VALUES
    (1, 1, '2025-12-01', '2025-12-15', 'borrowed'),
    (2, 2, '2025-12-02', '2025-12-16', 'borrowed');

EOF
}

menu 
````

### ⚠ Observação importante
`Este software foi desenvolvido para ajudar outros desenvolvedores Web, de forma totalmente gratuita.
É expressamente proibido vender, revender, comercializar ou lucrar de qualquer forma com este conteúdo.`
### 🐞 Encontrou algum bug?
`Se você achar qualquer erro, bug ou algo quebrado, por favor me avise!
Seu feedback ajuda a melhorar o projeto e manter tudo funcionando para todos. 🙏`
