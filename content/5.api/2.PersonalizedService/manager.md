---
title: Criar Tabela de Frete Personalizada
description: Endpoint para gerenciar a criação de tabelas de frete personalizadas.
icon: lucide:table
---

## 📌 Resumo

- **Método:** `POST`  
- **Endpoint:** `[URLBASE]/api/v1/shippingcustomtable/manager`  
- **Autenticação:** ✅ Requer token de acesso (Bearer)  
- **Categoria:** Shipping Custom Table  

---

## 📖 Descrição

Cria uma nova tabela de frete personalizada vinculada ao **tenant** autenticado.  

::alert{type="info"}
💡 Este endpoint deve ser usado por administradores ou sistemas autorizados para configurar regras de frete específicas.
::

---

## 📝 Parâmetros do Request

| Campo        | Tipo       | Obrigatório | Descrição                                                                 |
|--------------|------------|-------------|---------------------------------------------------------------------------|
| `name`       | string     | Sim         | Nome da tabela (mín. 3, máx. 100 caracteres).                             |
| `status`     | boolean    | Sim         | Status da tabela (ativo ou inativo).                                      |
| `item`       | array      | Sim         | Lista de itens da tabela (mín. 1 item).                                   |
| `createdAt`  | date       | Não         | Data de criação (gerada automaticamente caso não seja enviada).           |

> **item** segue o schema `ShippingCustomTableItemSchema`, contendo os campos necessários para cada regra da tabela.  

---

## 📤 Exemplo de Request


```json [POST [URLBASE]/api/v1/shippingcustomtable/manager]
{
  "name": "Tabela SP Capital",
  "status": true,
  "item": [
    {
      "cepInitial": "01001-000",
      "cepFinal": "05999-999",
      "shippingCost": 30.00,
      "minimumWeight": 0,
      "maximumWeight": 30,
      "increaseWeight": 2.50,
      "additionNfe": 5.00,
      "term": 4
    }
  ]
}
```
## 📥 Exemplo de Response

```json 200
{
    "data": {
        "id": "37711945-3f03-48bc-a9a8-161d7610c8cd"
    },
    "status": 200
}
```
