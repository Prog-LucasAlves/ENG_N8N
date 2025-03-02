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

## Estrutura do Projeto

```bash
|
|-- docker-compose.yml
|-- .env
|-- LICENSE
|-- README.md
```

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
      - N8N_BASIC_AUTH_ACTIVE=true
      - N8N_BASIC_AUTH_USER=${AUTH_USER}
      - N8N_BASIC_AUTH_PASSWORD=${AUTH_PASSWORD}
      - N8N_HOST=${SUBDOMAIN}.${DOMAIN_NAME}
      - N8N_PORT=5678
      - N8N_PROTOCOL=https
      - NODE_ENV=production
      - WWEBHOOK_URL=https://${SUBDOMAIN}.${DOMAIN_NAME}/
      - GENERIC_TIMEZONE=${GENERIC_TIMEZONE}
    volumes:
      - n8n_data:/home/node/.n8n
    ```

    Esta configuração define:

    - **n8n**:
      - Este serviço roda o n8n usando a imagem `n8nio/n8n`.
      - As variáveis de ambiente configuram a atenticação básica, definindo usuário e senha(`N8N_BASIC_AUTH_USER` e `N8N_BASIC_AUTH_PASSWORD`).
      - A porta `5678`é mapeada para o host para que você possa acessar o n8n no navegador.
    - **Volumas**:
      - O volume `n8n_data` garante que os dados do n8n sejam persistidos no seu sistema local.

3. **Crie o arquivo `.env`:**

   Esse arquivo pode ser usado para armazenar variáveis de ambiente sensíveis. Exemplo de conteúdo do arquivo `.env`:
   ```env
   N8N_BASIC_AUTH_ACTIVE=true
   N8N_BASIC_AUTH_USER=admin
   N8N_BASIC_AUTH_PASSWORD=admin
   N8N_HOST=localhost
   N8N_PORT=5678
   N8N_PROTOCOL=http
   N8N_PUBLIC_API_URL=http://localhost:5678/
   ```

4. **Execute o Docker Compose:**

   Na pasta contendo o `docker-compose.yml`, execute o seguinte comando para iniciar os serviços:
   ```bash
   docker-compose up -d
   ```

   Isso irá baixar as imagens Docker necesárias e iniciar os containers do n8n.

5. **Acesse o n8n:**

    Uma vez que os containers estejam rodando, você pode acessar o n8n abrindo um navegador e indo para:
    ```edge
    http://localhost:5678
    ```

    Faça login com as credenciais de **autenticação básica:**

    - **Usuário:** `admin`
    - **Senha:** `admin_password`

### **Parando os Serviços**

Para parar os serviços, execute:
```bash
docker-compose down
```

Isso irá parar e remover o container en execução, mas seus dados irão persistir na pasta `n8n_data`.

### **Solução de Problemas**

- Container não está iniciando? Verifique os logs para erros executando:

```bash
docker-compose logs
```

### **Contribuindo**

Contribuições para este projeto são bem-vindas! Se você encontrar algum problema ou quiser melhorar a configuração, fique à vontade para abrir um issue ou criar um pull request.

### **Licença**

Este projeto é licenciado sob a licença MIT, veja o arqquivo [LICENSE](https://github.com/Prog-LucasAlves/ENG_N8N/blob/main/LICENSE) para mais detalhes.
