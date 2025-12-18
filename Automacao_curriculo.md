# 📄 CurriculoDosGuri

Gerador simples de **currículo** e **mensagens para LinkedIn** via terminal.

Sem frescura. Sem promessa. Só o necessário.

---

## 🎯 Objetivo do Projeto

Facilitar a vida de quem está começando na área de tecnologia e precisa:

* Criar um currículo organizado
* Ter mensagens prontas para LinkedIn
* Se apresentar para recrutadores sem papo de coach

Tudo direto no terminal, usando **Bash**.

---

## ⚙️ O que o script faz

* 📄 Gera currículo em **Markdown**
* 💬 Gera mensagens de apresentação para LinkedIn
* 🧑‍💼 Gera mensagem simples para recrutadores
* 📘 Cria README do projeto automaticamente
* 📁 Organiza tudo em pastas

---

## 📁 Estrutura Gerada

```
CurriculoDosGuri/
├── curriculo/
│   └── curriculo.md
│
├── linkedin/
│   ├── Mensagem.md
│   └── Mensagem2.md
│
├── mensagens/
│   └── mensagem_recrutador.md
│
└── README.md
```

---

Escolha a opção desejada no menu:

```
1 - Gerar Currículo
2 - Gerar Mensagens LinkedIn
3 - Mensagem Para Recrutadores
4 - Gerar README do Projeto
0 - Sair
```

---

## 🛠️ Tecnologias

* Bash / Shell Script
* Markdown
* Linux / Terminal

---

## 🚧 Status do Projeto

🟡 Em construção

Ideia simples, funcional e aberta a melhorias.

---

```bash
echo "=========================="
echo "Gerador de Curriculos"
echo "CurriculoDosGuri"
echo "=========================="

BASE_DIR="$(pwd)/CurriculoDosGuri"
mkdir -p "$BASE_DIR"


gerar_curriculo(){
    mkdir -p "$BASE_DIR/curriculo"
    cat <<EOF > "$BASE_DIR/curriculo/curriculo.md"
# **NOME COMPLETO**

📍 Cidade / Estado  
📧 email@email.com  
📱 (00) 00000-0000  
🔗 GitHub: https://github.com/usuario  
🔗 LinkedIn: https://linkedin.com/in/usuario  

---

## 🎯 Objetivo
Breve descrição do objetivo profissional  
(ex: Estágio / Dev Júnior / Backend / Java / Web)

---

## 🧠 Resumo Profissional
Resumo curto (3–5 linhas):
- Quem você é
- O que estuda
- No que tem foco
- Onde quer chegar

---

## 🛠️ Habilidades Técnicas

**Linguagens**
- Java
- PHP
- JavaScript
- C#
- SQL

**Tecnologias & Ferramentas**
- Git / GitHub
- MySQL
- Linux
- Unity / Godot
- Docker (básico)

---

## 💼 Experiência Profissional

### **Empresa / Organização**
**Cargo** — Período  
- Atividade 1
- Atividade 2
- Atividade 3

---

## 🎓 Formação Acadêmica

**Curso** — Instituição  
Período

---

## 📚 Cursos Complementares

- Curso — Instituição (Ano)
- Curso — Instituição (Ano)

---

## 🚀 Projetos

**Nome do Projeto**  
- Descrição breve
- Tecnologias utilizadas
- Link (GitHub / Demo)

---

## 🌱 Conhecimentos em Andamento
- Tecnologia / Tema
- Tecnologia / Tema

---

## 📌 Informações Adicionais
- Disponibilidade
- Modalidade (remoto / presencial)
- Idiomas
EOF
}

gera_texto_linkdin(){
    mkdir -p "$BASE_DIR/linkedin"
    cat <<EOF > "$BASE_DIR/linkedin/Mensagem.md"
    Olá {{nome_pessoa}}, tudo bem?

Me chamo {{seu_nome}} e estou entrando em contato para me apresentar.
Atualmente estou estudando e desenvolvendo projetos práticos voltados à área de tecnologia, com foco em aprendizado contínuo e evolução profissional.

Tenho interesse em trocar experiências, aprender com quem já está na área e construir conexões de forma natural.
Sem promessas, sem venda — apenas conversa e troca de conhecimento.

Se fizer sentido, fico à disposição para conversar.
Obrigado pelo seu tempo!
EOF
cat <<EOF > "$BASE_DIR/linkedin/Mensagem2.md"
Fala {{nome_pessoa}}, tudo certo?

Sou {{seu_nome}}. Estou estudando tecnologia e criando alguns projetos por conta própria.
Nada comercial, só troca de ideia mesmo.

Se quiser, bora se conectar!
EOF
}

criador_mensagem_para_recrutador(){
    mkdir -p "$BASE_DIR/Mensagem"
    cat <<EOF > "$BASE_DIR/Mensagem/mensagem_recrutador.md"
    Olá {{nome}},
Sou {{seu_nome}} e estou iniciando minha carreira em desenvolvimento.
Vi seu perfil e achei interessante trocar uma ideia, sem compromisso.
Abraço!
EOF
}

readme_projeto(){
    cat <<EOF > "$BASE_DIR/README.md"
# 📄 CurriculoDosGuri

Gerador simples de currículo e mensagens para LinkedIn via terminal.

## O que faz:
- Gera currículo em Markdown
- Gera mensagens de apresentação
- Gera mensagem direta para recrutadores

Sem frescura. 
EOF

}

menu(){
    echo "1 - Gerar Currículo"
    echo "2 - Gerar Mensagens LinkedIn"
    echo "3 - Messagem Para Recrutadores"
    echo "4 - Readme me Projeto"
    echo "0 - Sair"
    read -p "Escolha: " op

    case $op in
        1) gerar_curriculo ;;
        2) gera_texto_linkdin ;;
        3) criador_mensagem_para_recrutador ;;
        4) readme_projeto ;;
        0) exit ;;
        *) echo "Opção inválida" ;;
    esac
}

while true; do
    menu
done
```

---

> Projeto criado para estudo, prática e automação do dia a dia.
> Sem marketing. Sem promessa. Só código útil.
