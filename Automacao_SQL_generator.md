# Automação | Gerador de SQL

Este repositório contém um Gerador de SQL que cria automaticamente bancos de dados e suas respectivas tabelas. O objetivo é fornecer scripts SQL prontos para uso em diferentes cenários, como sistemas de saúde, bibliotecas, hotelaria, e outros. Você pode usar esses scripts para criar bancos de dados com tabelas prontas para inserção de dados, relacionamentos e testes.

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

