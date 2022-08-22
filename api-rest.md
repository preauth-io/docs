---
description: >-
  Aprendamos cómo funciona el API. Sabemos que suele ser dolorosa esta parte,
  pero tranquila, estamos contigo para cualquier duda en devs@preauth.io
---

# API REST

{% hint style="success" %}
Únete a nuestro [_<mark style="color:blue;">espacio de Slack</mark>_](https://join.slack.com/t/preauth-soporte/shared\_invite/zt-18pzujyy8-F6cZBsHmZ\_5OZFd16fnnWw) y te ayudaremos con tus dudas
{% endhint %}

### Autenticación

Para tener acceso a los servicios es necesario haber obtenido el api-token para ser usado como cabecera en cada petición. Para más información, puedes revisar como obtener el api-token en la guía de [Primeros pasos](primeros-pasos.md#2-verifica-que-tengas-tu-api-token).

Cuando obtengas tu api-token, es necesario que lo envíes en la cabecera **"x-auth-token"** en cada petición que quieras hacer.

### Servicios

{% swagger method="post" path="/order" baseUrl="https://api.preauth.io/v1" summary="Crear orden" %}
{% swagger-description %}
Servicio para crear una orden, con el id de la orden luego podrás realizar la retención utilizando el 

[Widget](widget.md)

 
{% endswagger-description %}

{% swagger-parameter in="body" required="true" name="country" type="String" %}


[ISO 3166-1 alpha-2](https://en.wikipedia.org/wiki/ISO_3166-1_alpha-2#Officially_assigned_code_elements)

 (Ej: PE, CL, MX)
{% endswagger-parameter %}

{% swagger-parameter in="body" required="true" name="currency" type="String" %}


[ISO 4217](https://en.wikipedia.org/wiki/ISO_4217#Active_codes)

 (Ej: PEN, CLP, MXN)
{% endswagger-parameter %}

{% swagger-parameter in="body" required="true" name="amount" type="Integer" %}
Monto en la mínima denominación. Ejemplo: Dólares en centavos (para US$100, enviar 100000) y pesos chilenos en entero (para CLP$100, enviar 100)
{% endswagger-parameter %}

{% swagger-parameter in="body" required="true" name="reference" type="String" %}
Referencia del comercio
{% endswagger-parameter %}

{% swagger-parameter in="body" required="true" name="limit_date" type="String" %}
Fecha límite de la orden (YYYY-mm-dd)
{% endswagger-parameter %}

{% swagger-parameter in="body" name="meta.client.phone" type="String" %}
Formato

[ E.123](https://en.wikipedia.org/wiki/E.123#Example_formats)


{% endswagger-parameter %}

{% swagger-parameter in="header" name="x-auth-token" required="true" %}
Api token
{% endswagger-parameter %}

{% swagger-parameter in="body" name="meta.client.documentType" type="String" %}
Tipo de documento
{% endswagger-parameter %}

{% swagger-parameter in="body" name="meta.client.document" type="String" %}
Alfanumérico del documento
{% endswagger-parameter %}

{% swagger-parameter in="body" name="meta.client.email" type="String" %}
RFC 5322
{% endswagger-parameter %}

{% swagger-parameter in="body" name="meta.client.name" type="Stng" %}
Nombre del cliente
{% endswagger-parameter %}

{% swagger-parameter in="body" name="meta.product.title" type="String" %}
Nombre del producto/servicio
{% endswagger-parameter %}

{% swagger-parameter in="body" name="meta.billing.address" type="String" %}
Dirección del cliente
{% endswagger-parameter %}

{% swagger-parameter in="body" name="meta.billing.city" type="String" %}
Ciudad del cliente
{% endswagger-parameter %}

{% swagger-parameter in="body" name="meta.billing.region" type="String" %}
Región del cliente
{% endswagger-parameter %}

{% swagger-parameter in="body" name="meta.billing.country" type="String" %}
País del cliente
{% endswagger-parameter %}

{% swagger-response status="200: OK" description="Modelo Order" %}
```javascript
{
  "id": "4085-whOdSyS2FkGmm4j9feJNeMh0SjQDgLa5xAUENBkajsfQK",
  "reference": "order_00001",
  "currency": "PEN",
  "country": "PE",
  "limit_date": "2022-10-10",
  "amount": 15000,
  "status": "created",
  "pending_amount": 15000,
  "captured_amount": 0,
  "created_at": "2021-10-15 20:31:07",
  "updated_at": "2021-10-15 20:35:28"
}
```
{% endswagger-response %}
{% endswagger %}

{% swagger method="get" path="/order/{id}" baseUrl="https://api.preauth.io/v1" summary="Obtener orden" %}
{% swagger-description %}
Obtienes el objeto orden actualizado. Importante utilizarlo luego de recibir la confirmación de que se realizó la retención para verificar que la orden se encuentra en 

`in_progress`
{% endswagger-description %}

{% swagger-parameter in="header" name="x-auth-token" required="true" %}
Api token
{% endswagger-parameter %}

{% swagger-parameter in="query" name="id" required="true" %}
Id de la orden
{% endswagger-parameter %}

{% swagger-response status="200: OK" description="Modelo Order" %}
```javascript
{
  "id": "4085-whOdSyS2FkGmm4j9feJNeMh0SjQDgLa5xAUENBkajsfQK",
  "reference": "order_00001",
  "currency": "PEN",
  "country": "PE",
  "limit_date": "2022-10-10",
  "amount": 15000,
  "status": "in_progress",
  "pending_amount": 15000,
  "captured_amount": 0,
  "created_at": "2021-10-15 20:31:07",
  "updated_at": "2021-10-15 20:35:28"
}
```
{% endswagger-response %}
{% endswagger %}

{% swagger method="patch" path="/order/{id}" baseUrl="https://api.preauth.io/v1" summary="Actualizar orden" %}
{% swagger-description %}
Modifica el monto o la fecha límite de una orden creada. Solo cuando esté en 

`created`

 o 

`in_progress`
{% endswagger-description %}

{% swagger-parameter in="header" name="x-auth-token" required="true" %}
Api token
{% endswagger-parameter %}

{% swagger-parameter in="query" name="id" required="true" %}
Id de la orden
{% endswagger-parameter %}

{% swagger-parameter in="body" required="true" name="amount" type="Integer" %}
Monto en centavos, solo puede ser menor a order.pending_amount
{% endswagger-parameter %}

{% swagger-parameter in="body" required="true" name="limit_date" type="String" %}
Fecha límite de la orden, se puede editar según la fecha de expiración de la tarjeta asociada
{% endswagger-parameter %}

{% swagger-response status="200: OK" description="" %}
```javascript
{
  "status": "OK"
}
```
{% endswagger-response %}
{% endswagger %}

{% swagger method="delete" path="/order/{id}" baseUrl="https://api.preauth.io/v1" summary="Cancelar orden" %}
{% swagger-description %}
Devolverá el dinero retenido y la orden cambiará de estado a `canceled`.&#x20;

¡Importante!, una vez cancelada una orden no puede cambiar a otro estado, tendrás que crear una nueva orden desde cero.
{% endswagger-description %}

{% swagger-parameter in="header" name="x-auth-token" required="true" %}
Api token
{% endswagger-parameter %}

{% swagger-parameter in="query" name="id" required="true" %}
Id de la orden
{% endswagger-parameter %}

{% swagger-response status="200: OK" description="" %}
```javascript
{
  "status": "OK"
}
```
{% endswagger-response %}
{% endswagger %}

{% swagger method="post" path="/order/{id}/capture" baseUrl="https://api.preauth.io/v1" summary="Capturar orden" %}
{% swagger-description %}
Cobra todo o parte del dinero retenido, adicionalmente nos indicas si el monto sobrante quieres seguir reteniéndolo o lo liberarás. Ej: si tienes reservado $1000 y cobras $100, ¿qué quieres hacer con los $900 sobrantes? puedes seguir bloqueándolos o liberarlos, dependiendo del caso de uso que tengas.
{% endswagger-description %}

{% swagger-parameter in="header" name="x-auth-token" required="true" %}
Api token
{% endswagger-parameter %}

{% swagger-parameter in="query" name="id" required="true" %}
Id de la orden
{% endswagger-parameter %}

{% swagger-parameter in="body" required="true" name="amount" type="Integer" %}
Monto en centavos, solo puede ser menor o igual a order.pending_amount
{% endswagger-parameter %}

{% swagger-parameter in="body" required="true" name="keep_alive" type="Boolean" %}
Flag para preautorizar el monto restante
{% endswagger-parameter %}

{% swagger-response status="200: OK" description="" %}
```javascript
{
  "status": "OK"
}
```
{% endswagger-response %}
{% endswagger %}

### Modelos

#### Order

| Attributo       | Tipo        | Descripción                                                              | Ejemplo                                            |
| --------------- | ----------- | ------------------------------------------------------------------------ | -------------------------------------------------- |
| id              | Text        | Identificador de la orden                                                | 4085-whOdSyS2FkGmm4j9feJNeMh0SjQDgLa5xAUENBkajsfQK |
| reference       | Text        | Referencia del comercio                                                  | order\_0001                                        |
| currency        | Text        | ISO 4217                                                                 | PEN                                                |
| country         | Text        | ISO 3166-1 alpha-2                                                       | PE                                                 |
| limit\_date     | Text        | Fecha límite, pasada esta fecha se liberará el valor del pending\_amount | 2022-10-10                                         |
| amount          | Integer     | Monto en centavos                                                        | 15000                                              |
| status          | OrderStatus | Ver OrderStatus                                                          | created                                            |
| pending\_amount | Integer     | Monto en centavos de lo que debe mantenerse preautorizado                | 15000                                              |
| capture\_amount | Integer     | Monto en centavos de lo que se ha ido capturando                         | 0                                                  |
| created\_at     | Text        | Fecha de creación de la orden                                            | 2021-10-15 20:31:07                                |
| update\_at      | Text        | Última fecha de actualización de la orden                                | 2021-10-15 20:35:28                                |

#### OrderStatus

| Attributo      | Descripción                                                                  |
| -------------- | ---------------------------------------------------------------------------- |
| created        | Cuando la orden ha sido creada y aún no tiene un medio de pago asociado.     |
| in\_progress   | Cuando la orden ya cuenta con una tarjeta asociada.                          |
| canceled       | Cuando el comercio solicitó la cancelación.                                  |
| finished       | Cuando la fecha límite ya pasó.                                              |
| desynchronized | Cuando la tarjeta asociada a la orden no puede ser preautorizada nuevamente. |
