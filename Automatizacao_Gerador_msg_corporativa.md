# 🤖 Automação | Gerador de Mensagem Corporativa

Este repositório contém um script de automação para gerar mensagens corporativas em formato `.md` (Markdown), facilitando a criação de e-mails corporativos para diversas finalidades. O script oferece um menu interativo para escolher diferentes tipos de mensagens, como suporte técnico, agradecimentos, notificações, e mais.

## Funcionalidades

O **Gerador de Mensagem Corporativa** permite que você crie rapidamente os seguintes tipos de mensagens:

1. **Suporte Técnico**: Para enviar e-mails com instruções para os clientes encaminharem suas questões ao setor responsável.
2. **Agradecimento**: Mensagens formais de agradecimento após um contato ou interação com o cliente.
3. **Notificação de Reunião**: Para informar aos destinatários sobre o agendamento ou alteração de uma reunião.
4. **Aviso de Atualização**: Para avisar sobre atualizações de sistemas ou serviços programados.
5. **Confirmação de Cadastro**: E-mails confirmando o sucesso do cadastro de um usuário na plataforma.
6. **Recuperação de Senha**: Para enviar um link de recuperação de senha para o usuário.
7. **Agradecimento de Compra**: Para agradecer a compra do cliente e fornecer informações sobre o pedido.

## Como Usar

📚 Como Usar
- Crie uma pasta no seu computador.
- Dentro dela, crie um arquivo de texto comum.
- Cole o script completo fornecido no GitHub.
- Salve com a extensão:
- setup.sh
- Clique com botão direito → Executar com Git Bash
- Escolha as opções no menu e deixe a CLI trabalhar sozinha.

## Arquivos:
```Bash
mensagens/
  ├── agradecimento.md
  ├── agradecimento_compra.md
  ├── confirmacao_cadastro.md
  ├── notificacao_reuniao.md
  ├── recuperação_senha.md
  ├── suporte_tecnico.md
  └── aviso_atualizacao.md
````

## Script:

```bash
#!/bin/bash

echo ===============================
echo Gerador de Mensagem Corporativa
echo ===============================

# Base Directory
BASE_DIR="./mensagens"
mkdir -p "$BASE_DIR"

menu(){
    echo "Escolha o tipo de mensagem:"
    echo "1) Suporte Técnico"
    echo "2) Agradecimento"
    echo "3) Notificação de Reunião"
    echo "4) Aviso de Atualização"
    echo "5) Confirmação de Cadastro"
    echo "6) Recuperação de Senha"
    echo "7) Agradecimento de Compra"
    read -p "Digite a opção: " OPTION
}

generate_msg(){
    case $OPTION in
        1)
            cat <<EOF > "$BASE_DIR/suporte_tecnico.md"
# Suporte Técnico
Bom dia, por gentileza encaminhar o e-mail para o setor responsável.

## Agradecimento
Obrigado, bom dia!
EOF
            echo "Mensagem de Suporte Técnico gerada com sucesso!"
            ;;
        2)
            cat <<EOF > "$BASE_DIR/agradecimento.md"
# Agradecimento
Agradecemos o seu contato e ficamos à disposição para mais esclarecimentos.

## Agradecimento
Muito obrigado por sua atenção e confiança.
EOF
            echo "Mensagem de Agradecimento gerada com sucesso!"
            ;;
        3)
            cat <<EOF > "$BASE_DIR/notificacao_reuniao.md"
# Notificação de Reunião
Prezado(a),

Gostaríamos de informar que a reunião agendada para a data X foi confirmada.

## Detalhes da Reunião:
- **Data**: [Data da Reunião]
- **Hora**: [Hora da Reunião]
EOF
            echo "Mensagem de Notificação de Reunião gerada com sucesso!"
            ;;
        4)
            cat <<EOF > "$BASE_DIR/aviso_atualizacao.md"
# Aviso de Atualização
Informamos que o sistema será atualizado no próximo fim de semana. Durante este período, os serviços podem ser temporariamente interrompidos.

## Detalhes:
- **Data da Atualização**: [Data]
EOF
            echo "Mensagem de Aviso de Atualização gerada com sucesso!"
            ;;
        5) 
            cat <<EOF > "$BASE_DIR/confirmacao_cadastro.md"
# Confirmação de Cadastro

Prezado(a) [Nome],

Seu cadastro foi realizado com sucesso. Estamos felizes em tê-lo(a) conosco!

## Detalhes do Cadastro:
- **Nome:** [Nome]
- **Email:** [Email]

Acesse nossa plataforma e aproveite os recursos disponíveis!

Atenciosamente,  
[Nome da Empresa]
EOF
            ;;
        6) 
            cat <<EOF > "$BASE_DIR/recuperacao_senha.md"
# Recuperação de Senha

Olá [Nome],

Recebemos uma solicitação para redefinir sua senha. Para continuar, clique no link abaixo:

[Link para redefinir a senha]

Se você não solicitou essa alteração, por favor, ignore este e-mail.

Atenciosamente,  
[Nome da Empresa]
EOF
            ;;
        7) 
            cat <<EOF > "$BASE_DIR/agradecimento_compra.md"
# Agradecimento pela Sua Compra

Prezado(a) [Nome],

Obrigado pela sua compra na [Nome da Empresa]! Estamos processando o seu pedido e ele será enviado em breve.

## Detalhes do Pedido:
- **Pedido nº:** [Número do Pedido]
- **Produto(s):** [Lista de Produtos]
- **Total:** [Valor Total]
- **Data da Compra:** [Data da Compra]

Acompanhe o status do seu pedido em [Link de acompanhamento].

Atenciosamente,  
Equipe [Nome da Empresa]
EOF
            ;;
        *)
            echo "Opção inválida. Tente novamente."
            ;;
    esac
}

# Chama o menu para escolha do tipo de mensagem
menu
generate_msg
````
