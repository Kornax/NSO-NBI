---
title: NBI para NSO Empresariales

language_tabs: # must be one of https://git.io/vQNgJ
  - shell
  - python
  - javascript

toc_footers:
  - <a href='https://corp.antel.com.uy/wiki/display/NSO'>Wiki del Proyecto</a>
  - <a href='https://github.com/slatedocs/slate'>Documentation Powered by Slate</a>

includes:
  - errors

search: true
---

# Introducción

Para realizar las pruebas en NSO se creó un docker exclusivo para uso de SESE, dentro del mismo se cargaron los paquetes con el código de las consultas a probar.

<a href='https://corp.antel.com.uy/wiki/display/NSO'>Más Información en la wiki</a>

# Autenticación

El acceso es con una autenticación de usuario/contraseña. <a href='https://corp.antel.com.uy/wiki/display/NSO'>Ver Wiki</a>

# Altas

## Alta ONU

```python
import http.client
import mimetypes
conn = http.client.HTTPSConnection("{{IP_ADDRESS}}", {{PUERTO}})
payload = "{\r\n \"antel-pon-onu:onus\": [ {\r\n    \"olt\": \"{{OLT}}\",\r\n    \"rack\": \"{{RACK}}\",\r\n    \"shelf\": \"{{SHELF}}\",\r\n    \"slot\": \"{{SLOT}}\",\r\n    \"port\": \"{{PORT}}\",\r\n    \"onuid\": \"{{ONUID}}\",\r\n    \"technology\": \"{{TECHNOLOGY}}\",\r\n    \"slot-type\": \"{{SLOT_TYPE}}\",\r\n    \"autentication-mode\": \"password\",\r\n    \"password\": \"{{PASSWORD}}\"\r\n  }  ]\r\n}"
headers = {
  'Content-Type': 'application/yang-data+json',
  'Accept': 'application/yang-data+json',
  'Authorization': 'Basic cm9vdDpjaXNjbw==',
  'Content-Type': 'text/plain'
}
conn.request("POST", "/restconf/data/services/pon/infraestructure?no-out-of-sync-check", payload, headers)
res = conn.getresponse()
data = res.read()
print(data.decode("utf-8"))
```

```shell
curl --location --request POST 'http://{{IP_ADDRESS}}:{{PUERTO}}/restconf/data/services/pon/infraestructure?no-out-of-sync-check' \
--header 'Content-Type: application/yang-data+json' \
--header 'Accept: application/yang-data+json' \
--header 'Authorization: Basic cm9vdDpjaXNjbw==' \
--header 'Content-Type: text/plain' \
--data-raw '{
 "antel-pon-onu:onus": [ {
    "olt": "{{OLT}}",
    "rack": "{{RACK}}",
    "shelf": "{{SHELF}}",
    "slot": "{{SLOT}}",
    "port": "{{PORT}}",
    "onuid": "{{ONUID}}",
    "technology": "{{TECHNOLOGY}}",
    "slot-type": "{{SLOT_TYPE}}",
    "autentication-mode": "password",
    "password": "{{PASSWORD}}"
  }  ]
}'
```

```javascript

```

> The above command returns JSON structured like this:

```json

```

### HTTP Request

`GET http://IP_address:port/restconf/data/services/pon/infraestructure?no-out-of-sync-check`

### Parametros esperados

Parameter | Description
--------- | -----------
OLT  | Nombre de la OLT a configurar.
RACK | Rack del puerto PON.
SHELF | Shelf del puerto PON.
SLOT | Slot del puerto PON.
PORT | Puerto PON.
ONUID | Id de a ONU.


<aside class="success">
Ejemplo de comentario sobre un exito!
</aside>

<aside class="notice">
Esto es una nota importante!
</aside>

## Alta Base

## Alta Servicio Tipo 1

## Alta Servicio Tipo 2