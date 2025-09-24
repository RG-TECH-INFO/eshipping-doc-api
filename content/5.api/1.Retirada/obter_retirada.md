---
title: Obter Retirada
description: Endpoint para buscar uma retirada específica pelo ID.
icon: lucide:search
---

## 📌 Resumo

* **Método:** `POST`
* **Endpoint:** `[URLBASE]/api/v1/withdrawal`
* **Autenticação:** ✅ Requer token de acesso (Bearer)
* **Categoria:** Withdrawal

---

## 📖 Descrição

Retorna os detalhes de uma retirada específica, informando o `id` no corpo da requisição.
Caso o ID não exista, o retorno será `null`.

---

## 📝 Parâmetros do Request

| Campo | Tipo   | Obrigatório | Descrição                     |
| ----- | ------ | ----------- | ----------------------------- |
| `id`  | string | Sim         | ID da retirada (UUID válido). |

---

## 📂 Estrutura do Objeto `WithDrawalDTO`

| Campo          | Tipo    | Descrição                                                      |
| -------------- | ------- | -------------------------------------------------------------- |
| `id`           | string  | ID da retirada (UUID válido).                                  |
| `status`       | boolean | Status da retirada (ativo ou inativo).                         |
| `name`         | string  | Nome da retirada (mín. 3, máx. 50 caracteres).                 |
| `cepLocal`     | string  | CEP do local principal. Formato: `00000-000`.                  |
| `state`        | string  | Estado (UF). Apenas 2 caracteres (ex: `SP`).                   |
| `city`         | string  | Cidade da retirada (mín. 2 caracteres).                        |
| `address`      | string  | Endereço (mín. 3 caracteres).                                  |
| `neighborHood` | string  | Bairro (mín. 3 caracteres).                                    |
| `number`       | string  | Número do endereço.                                            |
| `shippingCost` | number  | Custo do envio. Não pode ser negativo.                         |
| `term`         | number  | Prazo de entrega em dias (inteiro > 0).                        |
| `cepInitial`   | string  | CEP inicial do intervalo de atendimento. Formato: `00000-000`. |
| `cepFinal`     | string  | CEP final do intervalo de atendimento. Formato: `00000-000`.   |
| `description`  | string  | Descrição da retirada (máx. 255 caracteres).                   |
| `created_at`   | date    | Data de criação da retirada.                                   |

---

## 📤 Exemplo de Request

```json [POST [URLBASE]/api/v1/withdrawal]
Authorization: Bearer <token_de_acesso>
Content-Type: application/json

{
  "id": "ccb175b5-b3ef-4129-b93b-f9d60137ace2"
}
```

---

## 📥 Exemplo de Response

```json [200 OK]
{
    "data": {
        "id": "ccb175b5-b3ef-4129-b93b-f9d60137ace2",
        "status": true,
        "name": "Centro de Distribuição SP",
        "cepLocal": "01001000",
        "state": "SP",
        "address": "Avenida Paulista",
        "number": "1234",
        "city": "São Paulo",
        "neighborHood": "Bela Vista",
        "shippingCost": 25.5,
        "term": 5,
        "cepInitial": "01001000",
        "cepFinal": "05999999",
        "description": "Ponto de retirada principal na cidade de São Paulo",
        "created_at": "2025-09-24T14:56:58.412Z"
    },
    "status": 200
}
```
