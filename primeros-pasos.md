# Primeros pasos

### 1 Registra tu compañía

Para comenzar a usar nuestro [API REST](api-rest.md) es necesario que completes nuestro[ formulario de registro](https://dashboard.preauth.io/register).

### 2 Verifica que tengas tu api-token

Para realizar tus pruebas verifica que tengas un api-token en el [apartado para desarrolladores](https://dashboard.preauth.io/panel/devs).

![](.gitbook/assets/image.png)

### 3 Crea tu primera orden

Para crear tu primera orden haz un request al método de crear orden de nuestro [API REST](api-rest.md).

```bash
curl -X POST  https://api.preauth.io/v1/order -H "Accept: application/json" -H "x-auth-token: token_test_a4a9f278n4c23f08e7e6" -H "content-type: application/json" -d "{\"currency\":\"PEN\",\"country\":\"PE\",\"amount\":15000,\"reference\":\"order_00001\",\"limit_date\":\"2022-10-10\"}"
```

Es importante que tengas en cuenta que el campo id es con el que podrás hacer las demás operaciones. Además, puedes ver que por el momento el estado de la orden es **"created"**. Para mayor detalle puedes revisar la documentación de nuestra [API REST](api-rest.md).

ORDER:

```json
{
  "id": "4085-whOdSyS2FkGmm4j9feJNeMh0SjQDgLa5xAUENBkajsfQK",
  "reference": "order_00001",
  "currency_id": "PEN",
  "country_id": "PE",
  "limit_date": "2022-10-10",
  "amount": 15000,
  "status": "created",
  "pending_amount": 15000,
  "captured_amount": 0,
  "created_at": "2021-10-15 20:31:07",
  "updated_at": "2021-10-15 20:31:07"
}
```

### 4 Muestra nuestro widget en tu web

#### 4.1 Carga nuestro SDK

```javascript
!function(e,t){window.PreauthObject=t,window[t]=window[t]||function(){(window[t].q=window[t].q||[]).push(arguments)};const n="script",o=document.createElement(n),c=document.getElementsByTagName(n)[0];o.async=1,o.src=e,c.parentNode.insertBefore(o,c)}("https://cdn.preauth.io/preauth.js","preauth");
```

#### 4.2 Configura el widget

```javascript
preauth("init", {
  order: "{{order_id}}",
  onSuccess() {
    //CODE
  },
  onError(e) {
    //CODE
  }
});
```

Se deben definir el {{order_id}} (obtenido en el paso 3) y las funciones que se ejecutarán en caso de error o éxito.

#### 4.3 Muestra el widget

```javascript
preauth("start");
```

Este paso hace que se le muestre el formulario de **preauth** al usuario de su web. Una vez que el usuario termine de ingresar la información de su tarjeta, el SDK invocará a la función **onSuccess **u **onError **según sea el caso. Para más información, puedes revisar la documentación de nuestro [widget](widget.md).

### 5 Verifica el estado de tu orden

```bash
curl -X GET  https://api.preauth.io/v1/order/4085-whOdSyS2FkGmm4j9feJNeMh0SjQDgLa5xAUENBkajsfQK -H "Accept: application/json" -H "x-auth-token: token_test_a4a9f278n4c23f08e7e6"
```

**ORDER:**

```json
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

Si todo ha salido bien, puedes verificar que el estado cambió a "in_progress" y la orden estará preautorizada hasta que se cumpla la fecha límite definida en el paso 3.