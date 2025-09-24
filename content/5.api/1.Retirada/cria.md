---
title: Criar Retirada
description: Endpoint para criar uma nova retirada (withdrawal).
icon: lucide:plus-circle
---


## 📌 Resumo

- **Método:** `POST`  
- **Endpoint:** `[URLBASE]/api/v1/withdrawal/create`  
- **Autenticação:** ✅ Requer token de acesso (Bearer)  
- **Categoria:** Withdrawal  

---

## 📖 Descrição

Cria uma nova retirada no sistema.  

::alert{type="info"}
💡 Este endpoint deve ser usado pelo **administrador** ou serviços autorizados para cadastrar pontos de retirada.
::

---

## 📝 Parâmetros do Request

| Campo          | Tipo     | Obrigatório | Descrição                                                                 |
|----------------|----------|-------------|---------------------------------------------------------------------------|
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
---

## 📤 Exemplo de Request

```json [POST [URLBASE]/api/v1/withdrawal/create]
{
  "status": true,
  "name": "Centro de Distribuição SP",
  "cepLocal": "01001-000",
  "state": "SP",
  "city": "São Paulo",
  "address": "Avenida Paulista",
  "neighborHood": "Bela Vista",
  "number": "1234",
  "shippingCost": 25.50,
  "term": 5,
  "cepInitial": "01001-000",
  "cepFinal": "05999-999",
  "description": "Ponto de retirada principal na cidade de São Paulo",
}
```

## Exemplo de Response

```json [RESPONSE [URLBASE]/api/v1/withdrawal/create]
{
    "data": {
        "id": "37711945-3f03-48bc-a9a8-161d7610c8cd"
    },
    "status": 200
}
```
