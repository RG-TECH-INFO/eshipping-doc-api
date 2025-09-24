---
title: Intruções de Erros
description: tratamento de erros e saidas
icon: lucide:shield-alert
---


## ✅ Padrão de Sucesso

Quando não ocorre erro, a API sempre retorna:

```json [RESPONSE [URLBASE]/api/v1/withdrawal/update]
{
  "status": 200,
  "data": { "id": "uuid" } // somente se tiver conteudo a retornar
}
```
---

## ⚠️ Estrutura de Erro

```json [ERRO]
{
  "error": "Mensagem descritiva do erro",
  "status": "[codigo]" // 409 | 403 | 401 | 500
}
```
---

## 🛑 Tipos de Erro

### 🔹 DomainError
- **Status:** 409  
- **Descrição:** Indica violação de regras de negócio.  

```json [RESPONSE [URLBASE]/api/v1/withdrawal/create]
{
  "error": "Nome muito curto",
  "status": 409
}
```

### 🔹 DomainToken
- **Status:** 403  
- **Descrição:** O token informado é inválido ou expirado.  

```json [RESPONSE [URLBASE]/api/v1/withdrawal]
{
  "error": "Token inválido ou expirado",
  "status": 403
}
```

### 🔹 DomainPlan
- **Status:** 401  
- **Descrição:** O cliente não possui plano válido para acessar este recurso.  

```json [RESPONSE [URLBASE]/api/v1/withdrawal/update]
{
  "error": "Plano expirado ou inválido",
  "status": 401
}
```

### 🔹 Erro Interno
- **Status:** 500  
- **Descrição:** Problema inesperado no servidor.  

```json [RESPONSE [URLBASE]/api/v1/withdrawal/delete]
{
  "error": "Erro interno do servidor.",
  "status": 500
}
```
