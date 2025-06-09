# 💸 Plataforma de Transferências Simplificada

Uma API RESTful para transferências financeiras entre usuários, com regras claras, separação por tipo de usuário e integrações externas simuladas.

---

## ⚙️ Tecnologias e Liberdade de Stack

Você pode usar **qualquer linguagem ou framework** com o qual se sinta confortável.

> O mais importante é que o projeto seja **estruturado com clareza**, boas práticas e organização.

---

## 🧭 Objetivo

Criar uma **API de transferências** que permita movimentações entre dois tipos de usuários:

- 👤 **Usuário comum**: envia e recebe valores
- 🏬 **Lojista**: apenas recebe valores

---

## 📋 Regras de Negócio

- Cada usuário deve ter:
  - Nome completo
  - CPF (único)
  - E-mail (único)
  - Senha
- Lojistas **não podem realizar transferências**
- Antes da transferência:
  - Validar se o usuário tem saldo
  - Chamar serviço externo de autorização:
    ```http
    GET https://util.devi.tools/api/v2/authorize
    ```
- A transação deve ser **atômica** (rollback em erro)
- Após sucesso, notificar o recebedor via:
    ```http
    POST https://util.devi.tools/api/v1/notify
    ```

---

## 📨 Exemplo de Requisição

```http
POST /transfer
Content-Type: application/json

{
  "value": 100.0,
  "payer": 4,
  "payee": 15
}
```

## 🧠 Boas Práticas Recomendadas
Separação clara por camadas (ex: controller, service, repository)

- Versionamento com Git + commits descritivos
- Tratamento de exceções
- Testes unitários e de integração
- Uso de Docker (diferencial)
- Documentação dos endpoints (Swagger/Postman/README)

##🛠️ Recursos úteis
Refactoring Guru

- PSR-12 Coding Style Guide
- Martin Fowler – Microservices
- Guzzle HTTP Client (caso use PHP)
- Tutorial RESTful

## ✅ Dicas finais
Foque na clareza e manutenibilidade do código

- Documente suas decisões e organização
- Deixe fácil para outras pessoas executarem seu projeto (instruções claras)
