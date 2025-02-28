# n8n Workflow Automation

O n8n é uma ferramenta de automação de fluxos de trabalho de código aberto que permite automatizar tarefas e integrar com mais de 200+ serviços, como bancos de dados, APIs, serviços de nuvem e muito mais. Este repositório contém a configuração para executar o **n8n** usando Docker e Docker Compose.

## Funcionalidades

- **Low-code**: Não é necessário escrever código complexo para criar fluxos de trabalho.
- **Flexível**: Integração com mais de 200 aplicativos e serviços (ex: Google Sheets, Slack, GitHub, etc.).
- **Auto-hospedado**: Controle total sobre seus fluxos de trabalho de automação.
- **Segurança**: Opção para autenticação básica e outros recursos de segurança.
- **Escalável**: Escale facilmente seus fluxos de trabalho conforme necessário.

## Pré-requisitos

- Docker
- Docker Compose

## Configuração com Docker

Este repositório fornece um arquivo `docker-compose.yml` para executar o **n8n** e seus serviços necessários em containers Docker.

### Instruções de Configuração

1. **Clone este repositório (ou crie seu próprio `docker-compose.yml`):**

   Se você estiver começando do zero, pode criar seu próprio `docker-compose.yml` ou clonar este projeto e navegar até a pasta do projeto:
   ```bash
   git clone https://github.com/Prog-LucasAlves/ENG_N8N.git
   cd n8n

2. **Crie o arquivo `docker-compose.yml`:**

    Abaixo está a estrutura para executar o **n8n** com Docker Compose:
    ```yml
    version: "3.8"

    services:
     n8n:
      image: n8nio/n8n:latest
      container_name: n8n
      restart: always
      ports:
       - "127.0.0.1:5678:5678"
    environment:
      - N8N_HOST=${SUBDOMAIN}.${DOMAIN_NAME}
      - N8N_PORT=5678
      - N8N_PROTOCOL=https
      - NODE_ENV=production
      - WWEBHOOK_URL=https://${SUBDOMAIN}.${DOMAIN_NAME}/
      - GENERIC_TIMEZONE=${GENERIC_TIMEZONE}
    volumes:
      - n8n_data:/home/node/.n8n
    ```

    :bulb: **Referência arquivo `.env` :arrow_right: [link](https://docs.n8n.io/hosting/installation/server-setups/docker-compose/#5-create-docker-compose-file)**

    Esta configuração define:

    - **n8n**: O serviço principal com autenticação básica ativada.

3. **Execute o Docker Compose:**

   Na pasta contendo o `docker-compose.yml`, execute o seguinte comando para iniciar os serviços:
   ```bash
   docker-compose up -d
   ```

   Isso irá baixar as imagens Docker necesárias e iniciar os containers do n8n.

4. **Acesse o n8n:**

    Uma vez que os containers estejam rodando, você pode acessar o n8n abrindo um navegador e indo para:
    ```edge
    http://localhost:5678
    ```

    Faça login com as credenciais de **autenticação básica:**

    - **Usuário:** `admin`
    - **Senha:** `admin_password`
