# API REST

### Autenticación

Para tener acceso a los servicios es necesario haber obtenido el api-token para ser usado como cabecera en cada petición. Para más información, puedes revisar como obtener el api-token en la guía de [Primeros pasos](primeros-pasos.md#2-verifica-que-tengas-tu-api-token).

Cuando obtengas tu api-token, es necesario que lo envíes en la cabecera **"x-auth-token"**.

### Servicios

#### Crear orden

{% swagger method="post" path="" baseUrl="https://api.preauth.io/v1/order" summary="" %}
{% swagger-description %}

{% endswagger-description %}

{% swagger-parameter in="body" required="true" name="country" type="" %}
country 
{% endswagger-parameter %}

{% swagger-parameter in="body" name="currency" required="true" %}
aaaa
{% endswagger-parameter %}

{% swagger-parameter in="query" name="" %}
order
{% endswagger-parameter %}

{% swagger-parameter in="header" name="x-auth-token" required="true" %}
Api token 
{% endswagger-parameter %}

{% swagger-parameter in="query" %}

{% endswagger-parameter %}

{% swagger-response status="200: OK" description="" %}
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

{% swagger method="get" path="" baseUrl="" summary="" %}
{% swagger-description %}

{% endswagger-description %}
{% endswagger %}

#### Actualizar orden

{% swagger method="get" path="" baseUrl="" summary="" %}
{% swagger-description %}

{% endswagger-description %}
{% endswagger %}

#### Cancelar orden

{% swagger method="get" path="" baseUrl="" summary="" %}
{% swagger-description %}

{% endswagger-description %}
{% endswagger %}

#### Capturar orden

{% swagger method="get" path="" baseUrl="" summary="" %}
{% swagger-description %}

{% endswagger-description %}
{% endswagger %}

### Modelos
