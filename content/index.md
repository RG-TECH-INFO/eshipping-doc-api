---
title: eShipping API Documentation
navigation: false
---

::hero
---
announcement:
  title: 'API v1.0 Available'
  icon: '🚀'
  to: /api/configuration/shadcn-docs
actions:
  - name: Get Started
    to: /api/configuration/shadcn-docs
---

#title
eShipping API Documentation

#description
Complete API documentation for eShipping services. :br Explore endpoints, authentication, and integration guides.
::

::card
---
title: "Exemplo de Rota da API"
description: "Aqui está um exemplo de como usar nossa API para rastreamento de envios"
---

## Endpoint de Rastreamento

```http
GET /api/v1/tracking/{tracking_code}
```

### Parâmetros
- `tracking_code` (string): Código de rastreamento do envio

### Exemplo de Resposta

```json
{
  "success": true,
  "data": {
    "tracking_code": "ES123456789BR",
    "status": "in_transit",
    "current_location": "São Paulo, SP",
    "estimated_delivery": "2024-01-15",
    "events": [
      {
        "date": "2024-01-10T10:30:00Z",
        "status": "picked_up",
        "location": "Rio de Janeiro, RJ"
      },
      {
        "date": "2024-01-12T14:20:00Z",
        "status": "in_transit",
        "location": "São Paulo, SP"
      }
    ]
  }
}
```

### Códigos de Status
- `picked_up`: Encomenda coletada
- `in_transit`: Em trânsito
- `out_for_delivery`: Saiu para entrega
- `delivered`: Entregue
- `exception`: Problema no envio

::
