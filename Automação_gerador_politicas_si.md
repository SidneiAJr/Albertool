# Automação | Gerador de Politicas SI:

Este projeto é um **script em Bash** que automatiza a criação de **políticas de Segurança da Informação em formato Markdown**, organizadas em diretórios prontos para uso como documentação interna, wiki corporativa ou base de conhecimento.

O foco é **automatizar governança e documentação**, algo comum em ambientes profissionais de TI, Segurança, DevOps e Compliance.

---

## 🎯 Objetivo

- Automatizar a criação de políticas de Segurança da Informação
- Padronizar documentação em Markdown
- Facilitar manutenção, versionamento e uso em wikis (Git, GitLab, GitHub, etc)
- Servir como base para ambientes corporativos ou estudos pessoais

---

### 📌 Políticas Operacionais
- Política de Senhas
- Política de Prevenção contra SQL Injection
- Política de Prevenção contra Phishing

### 📚 Wiki de Segurança da Informação
- Conceitos básicos de Segurança da Informação
- Ameaças comuns
- Spoofing
- Boas práticas de segurança
- Criptografia (com comparativo de algoritmos)

---

🖥️ Como usar?
1️⃣ Crie um arquivo de texto
2️⃣ Cole o código acima
3️⃣ Salve como:

gerar_si.bat
4️⃣ Dê dois cliques no arquivo


## Script:

```bash
#!/bin/bash

BASE_DIR="$(pwd)/politicas"
mkdir -p "$BASE_DIR"
mkdir -p "$BASE_DIR/WikiSI"

# ===============================
# Funções de geração de políticas
# ===============================

gerar_politica_phishing() {
cat <<EOF > "$BASE_DIR/politica_antiphishing.md"
# Política de Prevenção contra Phishing

## Objetivo
Estabelecer diretrizes para prevenir ataques de phishing e proteger informações da organização.

## O que é Phishing
Phishing é uma técnica de engenharia social utilizada para induzir usuários a fornecer informações sensíveis, como senhas, dados pessoais ou credenciais de acesso.

## Boas Práticas
- Não clicar em links desconhecidos ou suspeitos
- Verificar o remetente do e-mail
- Nunca informar senhas por e-mail ou mensagens
- Utilizar autenticação de dois fatores (2FA) sempre que possível

## Exemplos Comuns
- E-mails com senso de urgência
- Mensagens solicitando atualização de dados
- Links encurtados ou domínios estranhos

## Procedimento em Caso de Suspeita
- Não interagir com a mensagem
- Comunicar imediatamente o setor de TI
- Registrar o incidente conforme política interna
EOF
}

gerar_politica_si() {
cat <<EOF > "$BASE_DIR/WikiSI/Seguranca_informacao.md"
# 🛡️ Segurança Cibernética — Conceitos Básicos

## 🎯 Objetivo
Entender os **fundamentos da segurança da informação** e como eles se aplicam no contexto digital moderno.

---

## 🧠 O que é Segurança Cibernética?

Segurança Cibernética é o **conjunto de práticas, tecnologias e processos** usados para **proteger sistemas, redes e dados** contra acessos não autorizados, ataques ou danos.

Ela envolve **prevenção, detecção e resposta** a incidentes que possam comprometer a integridade, disponibilidade ou confidencialidade das informações.

---

## 🔺 Princípios Fundamentais (Tríade CIA)

| 🔒 Princípio | 💬 Descrição |
|---------------|--------------|
| **Confidencialidade** | Garantir que as informações sejam acessadas apenas por pessoas autorizadas. |
| **Integridade** | Garantir que os dados não sejam alterados indevidamente. |
| **Disponibilidade** | Garantir que os sistemas e informações estejam acessíveis quando necessários. |

---

## ⚙️ Áreas da Segurança Cibernética

1. **Segurança de Rede** – protege a infraestrutura contra invasões e ataques externos.  
2. **Segurança de Aplicações** – evita vulnerabilidades em softwares e sistemas.  
3. **Segurança de Dados** – protege informações armazenadas e transmitidas.  
4. **Segurança Operacional** – define políticas e permissões de acesso.  
5. **Conscientização do Usuário** – treina pessoas para reconhecer ameaças e agir com responsabilidade.

---

## 🔐 Exemplo Prático

> Um usuário recebe um e-mail com um anexo suspeito.  
> A segurança cibernética entra em ação quando:
> - O servidor bloqueia o e-mail automaticamente (prevenção)  
> - O antivírus detecta o arquivo malicioso (detecção)  
> - O time de TI investiga e corrige vulnerabilidades (resposta)

---

## 🧭 Conclusão

A segurança cibernética **não é apenas tecnologia** — é também **comportamento e cultura**.  
Cada ação preventiva, desde uma senha forte até uma política corporativa, faz parte de uma **defesa digital coletiva**.
EOF
}

gerar_politica_ameacas() {
cat <<EOF > "$BASE_DIR/WikiSI/ameacas_si.md"
# ⚠️ Ameaças Comuns na Segurança Cibernética

## 🎯 Objetivo
Conhecer os principais tipos de ameaças digitais e como elas podem comprometer sistemas e informações.
EOF
}

gerador_politica_spoofing() {
cat <<EOF > "$BASE_DIR/WikiSI/Spoofing.md"
# 🛡️ Cybersegurança — Spoofing: Guia de Defesa

## O que é Spoofing?

Spoofing é uma técnica usada por pessoas mal-intencionadas para **falsificar o número de origem** de uma ligação, mensagem ou e-mail.  
O golpista faz parecer que a chamada vem de um número confiável — às vezes, até do **seu próprio número** — para enganar o usuário e obter informações pessoais.

---

## 🚨 Quando isso acontece

- Você recebe **ligações do seu próprio número**.  
- Mensagens estranhas vindas de **contatos conhecidos**, mas com comportamento suspeito.  
- E-mails que parecem legítimos, mas pedem **dados pessoais ou bancários**.  

---

## 🧠 O que fazer

1. **Não atenda** ligações vindas do seu próprio número.  
2. **Nunca compartilhe** senhas, códigos de autenticação ou dados bancários.  
3. **Bloqueie** o número imediatamente no seu celular.  
4. **Entre em contato com a operadora** e registre uma reclamação sobre spoofing.  
5. **Faça um Boletim de Ocorrência (B.O.)** se houver suspeita de golpe.  
6. **Monitore** suas contas e troque senhas, caso desconfie de vazamento de dados.

---

## 🧰 Dica extra

Use **autenticação de dois fatores (2FA)** e mantenha seus dispositivos **atualizados**.  
Golpistas exploram brechas em sistemas antigos para realizar spoofing e phishing.

> ⚠️ Lembre-se: Spoofing é uma forma moderna de fraude.  
> Informação e cautela são suas melhores defesas.
EOF
}

gerador_politicas_sql_injection() {
cat <<EOF > "$BASE_DIR/Sql_injection.md"
# 🔐 Política de Prevenção contra SQL Injection

## Objetivo
Estabelecer diretrizes para prevenir ataques de SQL Injection em aplicações e sistemas que utilizam bancos de dados relacionais.

## O que é SQL Injection
SQL Injection é uma vulnerabilidade que ocorre quando dados fornecidos pelo usuário são inseridos diretamente em consultas SQL sem validação adequada, permitindo execução de comandos maliciosos no banco de dados.

## Impactos Potenciais
- Vazamento de dados sensíveis
- Modificação ou exclusão de informações
- Escalada de privilégios
- Comprometimento total do sistema

## Diretrizes de Prevenção

### 1️⃣ Uso de Prepared Statements
- Utilizar **consultas parametrizadas** (Prepared Statements)
- Nunca concatenar strings para formar queries SQL

### 2️⃣ Validação de Entrada
- Validar e sanitizar todos os dados recebidos do usuário
- Aplicar listas de permissão (whitelist) em vez de listas de bloqueio

### 3️⃣ Princípio do Menor Privilégio
- Contas de banco devem ter apenas permissões necessárias
- Proibir uso de contas administrativas em aplicações

### 4️⃣ Tratamento de Erros
- Não exibir mensagens de erro do banco para o usuário final
- Registrar erros em logs internos protegidos

### 5️⃣ Atualizações e Patches
- Manter SGBDs, ORMs e frameworks atualizados
- Aplicar correções de segurança assim que disponíveis

## Exemplos de Ataque
- `' OR 1=1 --`
- `'; DROP TABLE users; --`

## Procedimento em Caso de Incidente
1. Isolar a aplicação afetada
2. Analisar logs de acesso e banco
3. Corrigir falha identificada
4. Realizar teste de segurança antes de reimplantar

## Conclusão
A prevenção contra SQL Injection depende de boas práticas de desenvolvimento seguro, revisão de código e monitoramento contínuo.

EOF
}

gerador_politicas_senhas() {
cat <<EOF > "$BASE_DIR/Senhas.md"
# 🔐 Política de Senhas

## 1. Objetivo
Estabelecer diretrizes para criação, uso, armazenamento e gerenciamento de senhas, visando proteger o acesso a sistemas, aplicações e informações da organização.

## 2. Abrangência
Esta política se aplica a todos os colaboradores, prestadores de serviço, sistemas internos, aplicações web, APIs e qualquer recurso que exija autenticação.

## 3. Requisitos de Criação de Senhas

## 4. Validade e Troca de Senhas

- As senhas devem ser alteradas a cada **90 dias**
- É proibida a reutilização das **últimas 5 senhas**
- Troca imediata é obrigatória em caso de:
  - Suspeita de comprometimento
  - Incidente de segurança
  - Compartilhamento indevido

  ## 5. Armazenamento Seguro

- Senhas **nunca devem ser armazenadas em texto plano**
- É obrigatório o uso de:
  - Hash seguro (ex: `bcrypt`, `argon2`, `PBKDF2`)
- Credenciais devem ser armazenadas de forma protegida, com controle de acesso restrito

## 6. Uso de Gerenciadores de Senha

- É **fortemente recomendado** o uso de gerenciadores de senhas confiáveis
- Exemplos: Bitwarden, 1Password, KeePass
- Senhas não devem ser anotadas em papel ou arquivos não protegidos

É expressamente proibido:

- Compartilhar senhas com terceiros
- Reutilizar senhas pessoais em ambientes corporativos
- Enviar senhas por e-mail, mensagens ou aplicativos de chat
- Armazenar senhas em navegadores sem proteção adequada

EOF
}

si_boas_praticas(){
    cat <<EOF > "$BASE_DIR/WikiSI/Boas_Praticas.md"
    # 🧰 Boas Práticas de Defesa em Segurança Cibernética

## 🎯 Objetivo
Aprender **como se proteger contra ataques e reduzir vulnerabilidades** em sistemas, redes e dispositivos pessoais.

---

## 🧠 1️⃣ Princípio da Prevenção

A melhor defesa é **evitar o ataque antes que ele aconteça**.  
Boas práticas reduzem drasticamente os riscos de incidentes de segurança.

---

## 🔐 2️⃣ Senhas Fortes e Gerenciamento de Acesso

### ✅ Boas práticas:
- Criar **senhas longas e únicas** (mínimo 12 caracteres).  
- Misturar letras maiúsculas, minúsculas, números e símbolos.  
- **Nunca reutilizar** senhas entre sites.  
- Usar **gerenciadores de senhas** (como Bitwarden ou KeePass).  
- Ativar **autenticação em dois fatores (2FA)** sempre que possível.

> 💡 Exemplo de senha segura:  
> `H@ckTh3Futur3_2025!`

---

## 🧱 3️⃣ Atualizações e Patches de Segurança

Manter o sistema e os programas **sempre atualizados** é essencial.  
As atualizações corrigem vulnerabilidades que podem ser exploradas por invasores.

**Checklist de atualização:**
- 💻 Sistema operacional  
- 🌐 Navegadores  
- 📦 Aplicativos instalados  
- 🧰 Plugins e extensões  
- 🧠 Antivírus e firewall

---

## 🧭 4️⃣ Uso Seguro da Internet

| ⚙️ Boa Prática | 🧩 Descrição |
|----------------|-------------|
| **Evite redes Wi-Fi públicas** | Prefira conexões com senha ou use VPN. |
| **Verifique o HTTPS** | Sites seguros exibem cadeado e protocolo HTTPS. |
| **Não clique em links suspeitos** | Sempre passe o mouse e confira o endereço real. |
| **Baixe softwares apenas de fontes oficiais** | Evita programas adulterados com malware. |

---

## 🧰 5️⃣ Backup e Recuperação

Fazer **backup regular dos dados** protege contra perdas acidentais, falhas ou ataques como ransomware.

### 📦 Tipos de Backup:
- **Local:** em HD externo ou servidor interno.  
- **Nuvem:** Google Drive, OneDrive, Dropbox, etc.  
- **Híbrido:** combinação de ambos.

> 💡 Regra 3-2-1 de Backup:
> - 3 cópias dos dados  
> - 2 mídias diferentes  
> - 1 cópia fora do local principal

---

## 🧍‍♂️ 6️⃣ Conscientização e Educação Digital

A **segurança começa pelas pessoas**.  
Treinar usuários e colaboradores é tão importante quanto instalar antivírus.

**Boas práticas de comportamento digital:**
- Desconfiar de mensagens urgentes pedindo ação imediata.  
- Nunca compartilhar senhas.  
- Evitar divulgar informações pessoais publicamente.  
- Participar de treinamentos de segurança.

---

## 🧩 7️⃣ Ferramentas Básicas de Proteção

| 🧰 Ferramenta | 🛡️ Função |
|---------------|-----------|
| **Antivírus** | Detecta e bloqueia malwares conhecidos. |
| **Firewall** | Controla o tráfego de rede e bloqueia conexões suspeitas. |
| **VPN (Rede Privada Virtual)** | Criptografa o tráfego de dados em redes públicas. |
| **Monitor de Sistema** | Observa processos ativos e consumo de rede. |

---

## 🚨 8️⃣ Plano de Resposta a Incidentes

Mesmo com boas práticas, incidentes podem ocorrer.  
Um **plano de resposta** ajuda a reagir rapidamente e reduzir danos.

### 📋 Etapas:
1. **Identificação:** detectar o problema.  
2. **Contenção:** isolar sistemas afetados.  
3. **Erradicação:** remover a ameaça.  
4. **Recuperação:** restaurar o ambiente.  
5. **Análise Pós-incidente:** aprender e fortalecer defesas.

---

## 🧭 Conclusão

A segurança digital é uma **responsabilidade contínua**.  
Mais importante do que reagir a ataques, é **criar uma cultura preventiva**.

> 🔐 “A melhor defesa é o conhecimento.”  
> — Princípio básico da segurança cibernética.
EOF
}

si_criptografia(){
    cat <<EOF > "$BASE_DIR/WikiSI/Criptografia.md"
    # 🔐 Criptografia

A **criptografia** é o processo de proteger dados através de técnicas matemáticas que tornam as informações ilegíveis para quem não possuir a chave correta.

É usada para:
- Garantir **confidencialidade**, **integridade** e **autenticidade** de informações.  
- Proteger dados em trânsito (como HTTPS) e em repouso (bancos de dados, backups, etc).

---

## 🧱 Tipos de Criptografia

### 1. Criptografia Simétrica (ex: AES)
- Usa **a mesma chave** para criptografar e descriptografar.
- Rápida e eficiente.
- Exemplo: **AES (Advanced Encryption Standard)** — usado em VPNs, Wi-Fi (WPA2) e arquivos zip protegidos.


# 🧮 Quadro Comparativo de Métodos de Criptografia

| Categoria | Algoritmo | Tipo de Chave | Reversível? | Tamanho de Chave Comum | Uso Típico |
|------------|------------|----------------|--------------|------------------------|-------------|
| **Simétrica** | **AES (Advanced Encryption Standard)** | Mesma chave | ✅ Sim | 128 / 192 / 256 bits | VPN, Wi-Fi, discos |
| **Simétrica** | **DES (Data Encryption Standard)** | Mesma chave | ✅ Sim | 56 bits | Legado (obsoleto) |
| **Simétrica** | **3DES (Triple DES)** | Mesma chave (3x) | ✅ Sim | 168 bits | Sistemas legados |
| **Simétrica** | **Blowfish** | Mesma chave | ✅ Sim | 32–448 bits | Substituto do DES |
| **Simétrica** | **Twofish** | Mesma chave | ✅ Sim | 128 / 256 bits | Criptografia geral |
| **Assimétrica** | **RSA (Rivest–Shamir–Adleman)** | Pública / Privada | ✅ Sim | 1024–4096 bits | HTTPS, assinaturas |
| **Assimétrica** | **ECC (Elliptic Curve Cryptography)** | Pública / Privada | ✅ Sim | 256 bits ≈ RSA 3072 | Mobile, IoT |
| **Assimétrica** | **DSA (Digital Signature Algorithm)** | Pública / Privada | ✅ Sim | 1024–3072 bits | Assinaturas digitais |
| **Hashing** | **MD5** | Sem chave | ❌ Não | 128 bits | Checksum (não seguro) |
| **Hashing** | **SHA-1** | Sem chave | ❌ Não | 160 bits | Antigo (não recomendado) |
| **Hashing** | **SHA-256 / SHA-512** | Sem chave | ❌ Não | 256 / 512 bits | Integridade, senhas |
| **Hashing** | **bcrypt / Argon2** | Sem chave | ❌ Não | Variável | Armazenamento seguro de senhas |
| **Híbrido** | **PGP / GPG (Pretty Good Privacy / GNU Privacy Guard)** | Combina simétrica + assimétrica | ✅ Sim | Variável | Criptografia de e-mails e arquivos |
| **Fluxo** | **RC4** | Mesma chave | ✅ Sim | Variável | SSL antigo (inseguro) |
EOF
}

# ===============================
# Menu de seleção
# ===============================
menu() {
    echo "======================================="
    echo " Gerador de Políticas de SI em Markdown"
    echo "======================================="
    echo "Escolha a Opção:"
    echo "1) Base de Dados | Wiki Segurança da Informação"
    echo  "2) Gerar Politicas | Segurança da Informação"
    echo "0) Sair"
    read -p "Opção: " opcao

    case $opcao in
       1) gerar_politica_si 
          gerar_politica_ameacas
          gerador_politica_spoofing
          si_boas_praticas
          si_criptografia
          ;;
       2) gerador_politicas_senhas
          gerador_politicas_sql_injection
          gerar_politica_phishing
          ;;
    esac
}

# ===============================
# Execução do menu
# ===============================
menu
```
