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
Descrição: Banco de dados para um sistema de gestão de saúde, incluindo pacientes, médicos, consultas, diagnósticos e prescrições.
Tabelas Criadas:
patients: Armazena informações sobre os pacientes, como name, dob, gender, e contact_info.
doctors: Armazena informações sobre os médicos, como name, specialty, e contact_info.
appointments: Armazena informações sobre as consultas, com referências a patient_id e doctor_id.
diagnoses: Armazena os diagnósticos realizados para os pacientes, incluindo patient_id e diagnosis_description.
prescriptions: Armazena as prescrições médicas, com referência a appointment_id e informações sobre os medicamentos.

### 6. Banco de Dados: Hotelaria (Hospitality)

Descrição: Banco de dados para um sistema de gerenciamento de hotelaria, com informações sobre quartos, reservas, hóspedes e serviços do hotel.
Tabelas Criadas:
rooms: Armazena informações sobre os quartos do hotel, como room_number, room_type, price_per_night e status.
guests: Armazena informações sobre os hóspedes, como name, email, phone e address.
reservations: Armazena informações sobre as reservas feitas pelos hóspedes, com referência a guest_id e room_id.
services: Armazena informações sobre os serviços oferecidos pelo hotel, como service_name e price.
billing: Armazena informações de cobrança, incluindo os serviços consumidos durante a estadia e o valor total.
