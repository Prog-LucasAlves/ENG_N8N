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

Este repositório fornece um arquivo `docker-compose.yml` para executar o **n8n** e seus serviços necessários (como PostgreSQL) em containers Docker.

### Instruções de Configuração

1. **Clone este repositório (ou crie seu próprio `docker-compose.yml`):**

   Se você estiver começando do zero, pode criar seu próprio `docker-compose.yml` ou clonar este projeto e navegar até a pasta do projeto:
   ```bash
   git clone https://github.com/n8n-io/n8n.git
   cd n8
