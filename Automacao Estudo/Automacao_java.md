# Gerador de Arquivos POO Java | SQL

Este projeto é um **gerador automatizado de código em Java**, com foco em **Programação Orientada a Objetos (POO)** e **conexão com bancos de dados SQL**. O script facilita a criação de **arquivos Java** para estudos e projetos relacionados a **JDBC**, **CRUD** de banco de dados, **POJOs**, **JUnit para testes unitários**, e muito mais!

## Funcionalidades

O script oferece as seguintes opções para gerar arquivos Java automaticamente:

1. **Java | POO Estudo**:
   - Gera classes de estudo com várias interfaces e classes implementando-as.
   - Exemplo: Classes `teste1`, `teste2`, etc., com implementações para estudo de POO.

2. **Java | POO Banco SQL | COPIAR & COLAR**:
   - Gera um código Java para **conexão com bancos de dados SQL** usando **JDBC**.
   - Inclui um exemplo de **CRUD** (Create, Read, Update, Delete) para a manipulação de dados em um banco de dados.

## Como Usar
📚 Como Usar
- Crie uma pasta no seu computador.
- Dentro dela, crie um arquivo de texto comum.
- Cole o script completo fornecido no GitHub.
- Salve com a extensão:
- setup.sh
- Clique com botão direito → Executar com Git Bash
- Escolha as opções no menu e deixe a CLI trabalhar sozinha.

## Como Usar

1. **Pré-requisitos**:
   - **Java 8+** instalado no seu sistema.
   - **JDBC** configurado para o banco de dados desejado (por exemplo, MySQL ou PostgreSQL).

## Script:

````bash
#!/bin/bash

echo ==========================================
echo Gerador de Arquivos POO Java | SQL
echo ==========================================

BASE_DIR="./java_files"
mkdir -p "$BASE_DIR" 

menu(){
    echo "1) Java | POO Estudo"
    echo "2) Java | POO Banco SQL | COPIAR & COLAR"
    echo "3) Java | POO Jogo Teste CLI | COPIAR & COLAR"
    read -p "Digite a Opção: " OPTION
    case $OPTION in 
    1) create_study_poo ;;
    2) create_conecct_JDBC; create_conex_sql_POO_no_interface ;;
    *)
        echo "Opção inválida. Tente novamente."
        ;;
    esac
}

create_study_poo(){
    cat <<EOF >"$BASE_DIR/Study_poo.java"
package test;

public class Test {
    public static void main(String[] args) {     
    }
}

interface teste1{} // <------ Code Here
interface teste2{} // <------ Code Here
interface teste3{} // <------ Code Here
interface teste4{} // <------ Code Here
interface teste5{} // <------ Code Here
interface teste6{} // <------ Code Here

class teste7 implements teste1{} // <------ Code Here
class teste8 implements teste1{} // <------ Code Here
class teste9 implements teste1{} // <------ Code Here
class teste10 implements teste1{} // <------ Code Here
class teste11 implements teste1{} // <------ Code Here
class teste12 implements teste1{} // <------ Code Here
class teste13 implements teste1{}  // <------ Code Here
class teste14 implements teste1{} // <------ Code Here
EOF

    cat <<EOF > "$BASE_DIR/study_POO2.java"
public class Product {
    private int id;
    private String name;
    private double price;

    // Construtor
    public Product(int id, String name, double price) {
        this.id = id;
        this.name = name;
        this.price = price;
    }

    // Getters e Setters
    public int getId() {
        return id;
    }

    public void setId(int id) {
        this.id = id;
    }

    public String getName() {
        return name;
    }

    public void setName(String name) {
        this.name = name;
    }

    public double getPrice() {
        return price;
    }

    public void setPrice(double price) {
        this.price = price;
    }
}
EOF
}

create_conecct_JDBC(){
    cat <<EOF >"$BASE_DIR/conex_database_POO.java"
package test;
import java.sql.Connection;
import java.sql.DriverManager;
import java.sql.Statement;
import java.sql.ResultSet;
import java.sql.SQLException;

public class Test {
    public static void main(String[] args) { 
        InfoDatabase db = new InfoDatabase();
        db.connect();
        db.testConnection();
        db.disconnect();
    }   
}

interface VeryDatabase {
    void connect();
    void disconnect();
}

interface DatabaseTeste {
    void testConnection();
}

class InfoDatabase implements VeryDatabase, DatabaseTeste {
    @Override
    public void connect() {
        System.out.println("Conectando ao banco de dados...");
    }
    
    @Override
    public void disconnect() {
        System.out.println("Desconectando do banco de dados...");
    }
    
    @Override
    public void testConnection() {
        System.out.println("Testando a conexão...");
    }
}
EOF
}

create_conex_sql_POO_no_interface(){
    cat <<EOF > "$BASE_DIR/conex_sql_POO_no_interface.java"
import java.sql.Connection;
import java.sql.DriverManager;
import java.sql.SQLException;

public class DatabaseConnection {
    private static final String URL = "jdbc:mysql://localhost:3306/yourdb";
    private static final String USER = "root";
    private static final String PASSWORD = "";

    public static Connection connect() throws SQLException {
        return DriverManager.getConnection(URL, USER, PASSWORD);
    }

    public static void closeConnection(Connection conn) {
        try {
            if (conn != null && !conn.isClosed()) {
                conn.close();
            }
        } catch (SQLException e) {
            e.printStackTrace();
        }
    }
}
EOF
}

menu
````

