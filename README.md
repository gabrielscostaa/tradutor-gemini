# Tradutor Gemini — Sistema de Tradução Assíncrona

Este projeto implementa um sistema de tradução de textos baseado em uma arquitetura assíncrona, composto por dois serviços principais:

- **Translation API**: API REST que recebe e gerencia requisições de tradução.
- **Translation Worker**: Serviço que consome e processa as traduções enviadas para a fila.

## ✨ Funcionalidades

- Recebimento de textos para tradução via API REST.
- Processamento assíncrono de traduções com RabbitMQ.
- Acompanhamento do status de cada requisição.
- Integração com PostgreSQL para persistência dos dados.

## 📂 Estrutura do Projeto

```
.
├── translation-api/      # API REST para receber requisições de tradução
└── translation-worker/   # Serviço para processar traduções da fila
```

## ⚙️ Requisitos

- [Node.js 18+](https://nodejs.org/)
- [Docker](https://www.docker.com/) e [Docker Compose](https://docs.docker.com/compose/)
- [PostgreSQL](https://www.postgresql.org/)
- [RabbitMQ](https://www.rabbitmq.com/)

## 🚀 Como Rodar o Projeto

1. **Clone o repositório**
   ```bash
   git clone https://github.com/gabrielscostaa/tradutor-gemini.git
   cd tradutor-gemini
   ```

2. **Configure as variáveis de ambiente**
   - Copie o arquivo `.env.example` de cada serviço para `.env` e ajuste conforme necessário.

3. **Suba os serviços de infraestrutura**
   ```bash
   docker-compose up -d
   ```

4. **Inicie cada serviço separadamente**
   - No diretório de cada serviço (`translation-api/` e `translation-worker/`), execute:
     ```bash
     npm install
     npm run dev
     ```

## 📑 Endpoints da Translation API

- `POST /translations`  
  Envia um texto para tradução.
  - **Exemplo de body:**  
    ```json
    {
      "text": "Texto a ser traduzido",
      "targetLanguage": "en"
    }
    ```
- `GET /translations/:requestId`  
  Consulta o status e resultado de uma tradução.

## 🔄 Status Possíveis da Tradução

- `queued`: Aguardando na fila
- `processing`: Em processo de tradução
- `completed`: Tradução concluída
- `failed`: Falha no processo

## 🛠️ Exemplo de Uso

**Requisição de tradução:**
```bash
curl -X POST http://localhost:3000/translations \
  -H 'Content-Type: application/json' \
  -d '{"text": "Olá, mundo!", "targetLanguage": "en"}'
```

**Verificar status da tradução:**
```bash
curl http://localhost:3000/translations/{requestId}
```

## 🤝 Contribuindo

Contribuições são bem-vindas! Sinta-se à vontade para abrir issues e pull requests.

## 📄 Licença

Este projeto está licenciado sob a licença MIT.
