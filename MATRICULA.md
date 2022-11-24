## Listagem de Cartórios
Request
```
GET /onr/registry-office-list HTTP/1.1
Content-Type: application/json
Authorization: Bearer {TOKEN}
Host: https://api.revoluti.com.br
```

Response
```json
{
  "id": "00a9bbf9-7173-4b7e-90a1-0016ed7b04ce",
  "name": "registryOfficeList",
  "value": {
    "UF": {
      "CIDADE": [
        {
          "ID": "{CODIGO_CARTORIO}",
          "UF": "UF",
          "CNS": "000000",
          "Razao": "RAZAO SOCIAL",
          "Cidade": "CIDADE",
          "Estado": "ESTADO",
          "IDCidade": "0000",
          "IDEstado": 0,
          "NrCartorio": "00"
        },
        "...": "OUTROS CARTORIOS NA CIDADE"
      ]
    }
    }
}
```

## Criação da Auditoria
Request
```
POST /audits HTTP/1.1
Content-Type: application/json
Authorization: Bearer {TOKEN}
Host: https://api.revoluti.com.br
```
Body
```json
{
  "description": "DESCR",
  "type": "Property",
  "property": [{
    "registry_office": "{CODIGO_CARTORIO}",
    "registration_code": "1"
  }]
}
```

Response
```json
{
  "id": "{AUDIT_ID}", // armazenar
  "user_id": "bf71d272-f167-49ce-9d91-068df0c5ce4a",
  "type": "Property",
  "status": "Processing",
  "created_at": "2022-11-22T14:56:57.430Z",
  "updated_at": "2022-11-22T14:56:57.461Z",
  "finished_at": null,
  "reference": "2022.11.22.0014",
  "description": "Auditoria 001.000.0000-00",
  "config": null,
  "entities": [
    {
      "id": "dd7b1c77-41f6-4a1b-9df8-f1a09692e22f",
      "audit_id": "6e94f4f2-dd74-4b29-bab7-1f22e05f063c",
      "property_id": "51551161-eb3b-4139-8ed7-cefca5433053",
      "person_id": null,
      "entity_type": "property",
      "config": null,
      "created_at": "2022-11-23T23:55:14.167Z",
      "updated_at": "2022-11-23T23:55:14.163Z",
      "property": {
        "id": "51551161-eb3b-4139-8ed7-cefca5433053",
        "user_id": "bf71d272-f167-49ce-9d91-068df0c5ce4a",
        "state": null,
        "city": null,
        "registry_office": 1,
        "registration_code": "1",
        "taxpayer_code": null,
        "active": "Y",
        "address": null,
        "created_at": "2022-11-23T23:55:14.166Z",
        "updated_at": "2022-11-23T23:55:14.163Z"
      }
    }
  ]
}
```

## Consulta do Status da Auditoria

Request
```
GET /audits/{AUDIT_ID} HTTP/1.1
Content-Type: application/json
Authorization: Bearer {TOKEN}
Host: https://api.revoluti.com.br
```

Responses

