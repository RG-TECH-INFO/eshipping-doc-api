---
title: Atualizar Retirada
description: Endpoint para atualizar uma retirada existente.
icon: lucide:refresh-ccw
---

## 📌 Resumo

- **Método:** `POST`  
- **Endpoint:** `[URLBASE]/api/v1/withdrawal/update`  
- **Autenticação:** ✅ Requer token de acesso (Bearer)  
- **Categoria:** Withdrawal  

---

## 📖 Descrição

Atualiza os dados de uma retirada já existente no sistema.  

::alert{type="warning"}
⚠️ Este endpoint **não cria** novas retiradas. Ele apenas **atualiza** uma já existente, sendo obrigatório informar o `id`.  
::

---

## 📝 Parâmetros do Request

| Campo          | Tipo     | Obrigatório | Descrição                                                                 |
|----------------|----------|-------------|---------------------------------------------------------------------------|
| `id`           | string   | Sim         | ID da retirada (UUID válido).                                             |
| `status`       | boolean  | Sim         | Status da retirada (ativo ou inativo).                                    |
| `name`         | string   | Sim         | Nome da retirada (mín. 3, máx. 50 caracteres).                            |
| `cepLocal`     | string   | Sim         | CEP do local principal. Formato: `00000-000`.                             |
| `state`        | string   | Sim         | Estado (UF). Apenas 2 caracteres (ex: `SP`).                              |
| `city`         | string   | Sim         | Cidade da retirada (mín. 2 caracteres).                                   |
| `address`      | string   | Sim         | Endereço (mín. 3 caracteres).                                             |
| `neighborHood` | string   | Sim         | Bairro (mín. 3 caracteres).                                               |
| `number`       | string   | Sim         | Número do endereço.                                                       |
| `shippingCost` | number   | Sim         | Custo do envio. Não pode ser negativo.                                    |
| `term`         | number   | Sim         | Prazo de entrega em dias (inteiro > 0).                                   |
| `cepInitial`   | string   | Sim         | CEP inicial do intervalo de atendimento. Formato: `00000-000`.            |
| `cepFinal`     | string   | Sim         | CEP final do intervalo de atendimento. Formato: `00000-000`.              |
| `description`  | string   | Não         | Descrição da retirada (máx. 255 caracteres).                              |
| `created_at`   | date     | Não         | Data de criação (geralmente preenchida pelo sistema).                     |

---

## 📤 Exemplo de Request

```json [POST [URLBASE]/api/v1/withdrawal/update]
{
  "id": "37711945-3f03-48bc-a9a8-161d7610c8cd",
 "status": false,
  "name": "Retirada Centro são paulo",
  "cepLocal": "01001-000",
  "state": "SP",
  "city": "São Paulo",
  "address": "Av. Brigadeiro Luís Antônio",
  "neighborHood": "Bela Vista",
  "number": "1200",
  "shippingCost": 30,
  "term": 4,
  "cepInitial": "01000-000",
  "cepFinal": "05999-999",
  "description": "Atualização do ponto de retirada central"
}

```

```json [RESPONSE [URLBASE]/api/v1/withdrawal/update]
{
  "status": 200
}

```