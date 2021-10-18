# API REST

### Autenticación

Para tener acceso a los servicios es necesario haber obtenido el api-token para ser usado como cabecera en cada petición. Para más información, puedes revisar como obtener el api-token en la guía de [Primeros pasos](primeros-pasos.md#2-verifica-que-tengas-tu-api-token).

Cuando obtengas tu api-token, es necesario que lo envíes en la cabecera **"x-auth-token"**.

### Servicios

#### Crear orden

{% swagger method="post" path="/order" baseUrl="https://api.preauth.io/v1" summary="" %}
{% swagger-description %}
{% endswagger-description %}

{% swagger-parameter in="body" required="true" name="country" type="String" %}
ISO 3166-1 alpha-2
{% endswagger-parameter %}

{% swagger-parameter in="body" required="true" name="currency" type="String" %}
ISO 4217
{% endswagger-parameter %}

{% swagger-parameter in="body" required="true" name="amount" type="Integer" %}
Monto en centavos
{% endswagger-parameter %}

{% swagger-parameter in="body" required="true" name="reference" type="String" %}
Referencia del comercio
{% endswagger-parameter %}

{% swagger-parameter in="body" required="true" name="limit_date" type="String" %}
Fecha límite de la orden
{% endswagger-parameter %}

{% swagger-parameter in="header" name="x-auth-token" required="true" %}
Api token 
{% endswagger-parameter %}

{% endswagger-parameter %}

{% swagger-response status="200: OK" description="Modelo Order" %}
```javascript
{
  "id": "4085-whOdSyS2FkGmm4j9feJNeMh0SjQDgLa5xAUENBkajsfQK",
  "reference": "order_00001",
  "currency_id": "PEN",
  "country_id": "PE",
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

#### Obtener orden

{% swagger method="get" path="/order/{id}" baseUrl="https://api.preauth.io/v1" summary="" %}
{% swagger-description %}
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
  "currency_id": "PEN",
  "country_id": "PE",
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

#### Actualizar orden

{% swagger method="patch" path="/order/{id}" baseUrl="https://api.preauth.io/v1" summary="" %}
{% swagger-description %}
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

{% swagger-response status="200: OK" description="Modelo Order" %}
```javascript
{
  "id": "4085-whOdSyS2FkGmm4j9feJNeMh0SjQDgLa5xAUENBkajsfQK",
  "reference": "order_00001",
  "currency_id": "PEN",
  "country_id": "PE",
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

#### Cancelar orden

{% swagger method="delete" path="/order/{id}" baseUrl="https://api.preauth.io/v1" summary="" %}
{% swagger-description %}
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
  "message": "The order will be canceled in a few moments."
}
```
{% endswagger-response %}
{% endswagger %}

#### Capturar orden

{% swagger method="post" path="/order/{id}/capture" baseUrl="https://api.preauth.io/v1" summary="" %}
{% swagger-description %}
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

{% swagger-response status="200: OK" description="Modelo CaptureResult" %}
```javascript
{
  "status": "OK",
  "messages": []
}
```
{% endswagger-response %}
{% endswagger %}

### Modelos
