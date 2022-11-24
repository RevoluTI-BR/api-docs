## Criação da Auditoria
Request
```
POST /audits/type/property-municipal-debts HTTP/1.1
Content-Type: application/json
Authorization: Bearer {TOKEN}
Host: https://api.revoluti.com.br
```
Body
```json
{
    "property": {
        "taxpayer_code": "001.000.0000-00", // obrigatório
	"city": "SÃO PAULO - CAPITAL" // único valor aceito
    }
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
	"documents": [
		{
			"id": "{DOCUMENT_ID}", // armazenar
			"user_id": "bf71d272-f167-49ce-9d91-068df0c5ce4a",
			"person_id": null,
			"transaction_id": null,
			"audit_id": "2f676193-c6f8-4be7-b1ec-cc21ab855465",
			"entity_id": "36eb3a6f-fb8c-4152-8c3a-b2208b3849cb",
			"entity": "property",
			"integrator": "plexi",
			"description": "Consulta Débitos de IPTU",
			"type": "prefeitura-sp/extrato-debitos-iptu",
			"subtype": null,
			"status": "pending",
			"details": {
				"sql": "001.000.0000-00"
			},
			"response": null,
			"review": null,
			"history": null,
			"extra": null,
			"try_count": null,
			"created_at": "2022-11-22T14:56:57.451Z",
			"updated_at": "2022-11-22T14:56:57.450Z"
		}
	]
}
```

## Consulta do Status do Documento

Request
```
GET /documents/{DOCUMENT_ID} HTTP/1.1
Content-Type: application/json
Authorization: Bearer {TOKEN}
Host: https://api.revoluti.com.br

```

Responses

- Documento ainda em processamento
```json
{
	"id": "612d5306-6f21-4add-b13e-88d5c9c6d3d6",
	"user_id": "bf71d272-f167-49ce-9d91-068df0c5ce4a",
	"person_id": null,
	"transaction_id": null,
	"audit_id": "2f676193-c6f8-4be7-b1ec-cc21ab855465",
	"entity_id": "36eb3a6f-fb8c-4152-8c3a-b2208b3849cb",
	"entity": "property",
	"integrator": "plexi",
	"description": "Consulta Débitos de IPTU",
	"type": "prefeitura-sp/extrato-debitos-iptu",
	"subtype": null,
	"status": "pending",
	"details": {
		"sql": "001.000.0000-00"
	},
	"response": null,
	"review": null,
	"history": null,
	"extra": null,
	"try_count": null,
	"created_at": "2022-11-22T14:56:57.451Z",
	"updated_at": "2022-11-22T14:56:57.450Z"
}
```

- Documento com débitos encontrados
```json
{
	"id": "51ea8d10-0570-4ea0-a8ff-0cd814914aeb",
	"user_id": "bf71d272-f167-49ce-9d91-068df0c5ce4a",
	"person_id": null,
	"transaction_id": null,
	"audit_id": "3388e455-58f8-4aac-aa7b-63c0b6fd231a",
	"entity_id": "5448adec-f79a-43bf-b994-128d53b26605",
	"entity": "property",
	"integrator": "plexi",
	"description": "Consulta Débitos de IPTU",
	"type": "prefeitura-sp/extrato-debitos-iptu",
	"subtype": null,
	"status": "rejected",
	"details": {
		"sql": "081.345.0027-7"
	},
	"response": {
		"file": "{INTERNAL_USE}",
		"status": 200,
		"message": {
			"sql": "081.345.0027-7",
			"iptu": [
				{
					"nl": "1",
					"situacao": "EM ABERTO",
					"anoExercicio": 2022,
					"valorLancado": 5946.3,
					"valorDevidoAtualizado": 594.63
				}
			],
			"status": "positivo",
			"endereco": "R MIN AMERICO MARCO ANTONIO , 113 - CEP: 05442-040",
			"endpoint": "prefeitura-sp-extrato-debitos-iptu",
			"sqlAscendente": []
		},
		"request_id": "84cd2c7e-0b2a-4f4d-9ece-978372264a0d"
	},
	"review": {
		"description": "2022 - EM ABERTO: R$ 594,63"
	},
	"extra": null,
	"try_count": null,
	"created_at": "2022-10-27T16:38:00.468Z",
	"updated_at": "2022-10-27T16:49:01.482Z"
}
```

- Documento sem débitos encontrados
```json
{
	"id": "565dcea7-452b-40bb-aea4-05b7fea4fadc",
	"user_id": "bf71d272-f167-49ce-9d91-068df0c5ce4a",
	"person_id": null,
	"transaction_id": null,
	"audit_id": "b33a06ea-d4da-4b55-9a80-3273aa947472",
	"entity_id": "2a3afe71-6561-4223-8a92-ca709e490cfd",
	"entity": "property",
	"integrator": "plexi",
	"description": "Consulta Débitos de IPTU",
	"type": "prefeitura-sp/extrato-debitos-iptu",
	"subtype": null,
	"status": "approved",
	"details": {
		"sql": "300.005.0820-6"
	},
	"response": {
		"file": "{INTERNAL_USE}",
		"status": 200,
		"message": {
			"sql": "300.005.0820-6",
			"iptu": [],
			"status": "negativo",
			"endereco": "AV MAGALHAES DE CASTRO , 4800 CJ. 81 - TOR. 3 - CONTIN. TOWER - CD CEP: 05676-120",
			"endpoint": "prefeitura-sp-extrato-debitos-iptu",
			"sqlAscendente": []
		},
		"request_id": "6ae1daef-e8a0-4193-a187-33622235f9de"
	},
	"review": null,
	"extra": null,
	"try_count": null,
	"created_at": "2022-10-25T17:59:01.393Z",
	"updated_at": "2022-10-25T18:07:01.305Z"
}
```
- Problemas ao efetuar a consulta
```json
{
	"id": "9c516eb2-f97e-4604-8867-4aef37d9d2cb",
	"user_id": "bf71d272-f167-49ce-9d91-068df0c5ce4a",
	"person_id": null,
	"transaction_id": "1ef0efe5-c0c4-43f1-9499-8cff7d507d48",
	"audit_id": null,
	"entity_id": "9723d216-6b1c-43d4-977e-c1d006fb422a",
	"entity": "property",
	"integrator": "plexi",
	"description": "Consulta Débitos de IPTU",
	"type": "prefeitura-sp/extrato-debitos-iptu",
	"subtype": null,
	"status": "error",
	"details": {
		"sql": "067.024.0006-6"
	},
	"response": {
		"send": {
			"data": {
				"sql": "067.024.0006-6"
			}
		},
		"status": 422,
		"message": {
			"errors": {
				"sql": [
					"SQL inválido"
				]
			},
			"message": "The given data was invalid."
		}
	},
	"review": null,
	"extra": null,
	"try_count": null,
	"created_at": "2022-10-27T00:56:01.089Z",
	"updated_at": "2022-10-27T14:41:01.607Z"
}
```
