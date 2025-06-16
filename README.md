# Sistema de Tradução Assíncrono

Este projeto consiste em um sistema de tradução de textos que utiliza uma arquitetura assíncrona com dois serviços principais:

1. **Translation API**: API REST que recebe requisições de tradução
2. **Translation Worker**: Serviço consumidor que processa as traduções

## Estrutura do Projeto

```
.
├── translation-api/     # API REST para receber requisições
└── translation-worker/  # Serviço consumidor para processar traduções
```

## Requisitos

- Node.js 18+
- Docker e Docker Compose
- PostgreSQL
- RabbitMQ

## Configuração do Ambiente

1. Clone o repositório
2. Configure as variáveis de ambiente (ver .env.example em cada serviço)
3. Execute `docker-compose up` para iniciar os serviços de infraestrutura
4. Inicie cada serviço separadamente

## Serviços

### Translation API

API REST que recebe requisições de tradução e as envia para uma fila.

**Endpoints:**
- `POST /translations`: Envia texto para tradução
- `GET /translations/:requestId`: Consulta status da tradução

### Translation Worker

Serviço consumidor que processa as requisições de tradução da fila.

## Status das Traduções

- `queued`: Aguardando na fila
- `processing`: Em processo de tradução
- `completed`: Tradução concluída
- `failed`: Falha no processo # tradutor-gemini
# tradutor-gemini
