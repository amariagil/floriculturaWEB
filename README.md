# Projeto WEBAPI - Unidade 3

API de produtos (Floricultura) com:

- SQLite no lugar de array em memoria
- Camadas Repository -> Service -> Controller
- Pastas: config, models, repositories, services, controllers, routes, middlewares
- Login com access_token
- Sessao no SQLite com connect-sqlite3

Este projeto expoe **somente a API** (sem frontend).

## Como rodar

```bash
npm install
npm start
```

API: http://localhost:3000/

### Credencial (.env)

```
SESSION_SECRET=troque-este-segredo
ACCESS_TOKEN=token-secreto-da-aula
```

No login (`POST /api/login`), envie o token no body JSON, por exemplo:

```json
{
  "access_token": "token-secreto-da-aula"
}
```

## Estrutura

```
projetoWEBAPI/
  server.js
  .env
  database/           # app.db (produtos) e sessions.db (sessoes)
  src/
    app.js
    config/
    models/
    repositories/
    services/
    controllers/
    routes/
    middlewares/
  scripts/
    teste-secao14.js
```

## Mapa de rotas

| Metodo | Rota | Acesso |
|--------|------|--------|
| GET | / | Publica - info da API |
| POST | /api/login | Publica - cria sessao com access_token |
| GET | /api/perfil | Protegida |
| POST | /api/logout | Protegida |
| GET | /api/produtos | Publica |
| GET | /api/produtos/:id | Publica |
| POST | /api/produtos | Protegida |
| PUT | /api/produtos/:id | Protegida |
| DELETE | /api/produtos/:id | Protegida |

## Teste da secao 14

```bash
npm test
```

Valida:
1. criar produto -> reiniciar servidor -> produto continua
2. login com access_token -> reiniciar servidor -> sessao continua
