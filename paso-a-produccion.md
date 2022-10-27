---
description: >-
  En muy sencillos pasos podrás obtener la información necesaria para que
  podamos ayudarte a configurar tu cuenta y comenzar a usar Preauth
---

# Paso a producción

### Certificación

{% hint style="success" %}
Si solo usarás el dashboard omite este paso
{% endhint %}

Cuando hayas finalizado la integración programa con tu POC (point-of-contact) asignado de Preauth una certificación. Para tener una certificación exitosa, validaremos que los requests que estés enviando sean correctos y revisaremos en conjunto los response que estás recibiendo.

Esto lo hacemos para que puedas utilizar al máximo Preauth y tus clientes tengan la mejor experiencia posible.

{% hint style="warning" %}
En caso no sepas quien es tu POC escríbele a [sebastian@preauth.io](mailto:sebastian@preauth.io)
{% endhint %}

### Elige tu procesador de pagos

[Izipay](paso-a-produccion.md#izipay)

[Kushki](paso-a-produccion.md#kushki)

[d·local](paso-a-produccion.md#d-local)

[Stripe](paso-a-produccion.md#stripe)

[Mercadopago](paso-a-produccion.md#mercadopago)

[Conekta](paso-a-produccion.md#undefined)

{% hint style="info" %}
La información de tu procesador debes enviarla a [https://forms.gle/vuiaaBLRrUDCWJUb8](https://forms.gle/vuiaaBLRrUDCWJUb8)
{% endhint %}

### Izipay

Desde tu [_backoffice_ en Izipay](https://secure.micuentaweb.pe/vads-merchant/) puedes generar y obtener las credenciales para el ambiente de producción. En caso no tengas acceso debes consultarlo con tu Key Account Manager asignado por Izipay.

<figure><img src=".gitbook/assets/Screen Shot 2022-09-22 at 10.28.28.png" alt=""><figcaption><p>Generación y obtención de credenciales en el backoffice de Izipay</p></figcaption></figure>

{% hint style="info" %}
La información de tu procesador debes enviarla a [https://forms.gle/vuiaaBLRrUDCWJUb8](https://forms.gle/vuiaaBLRrUDCWJUb8)
{% endhint %}

### Kushki

Una vez estés listo para pasar a producción primero debemos certificar la integración en conjunto con Kushki, para eso debes contactarte a [integraciones@kushkipagos.com](mailto:integraciones@kushkipagos.com). Luego de aprobar la certificación, te enviarán tus credenciales para producción.

{% hint style="info" %}
La información de tu procesador debes enviarla a [https://forms.gle/vuiaaBLRrUDCWJUb8](https://forms.gle/vuiaaBLRrUDCWJUb8)
{% endhint %}

### d·local

En el [dashboard de dLocal](https://dashboard.dlocal.com/settings/integration) puedes obtener tus credenciales de producción. En caso no te aparezcan. Comunícate con [devs@preauth.io](mailto:devs@preauth.io) donde podemos coordinar con nuestros Key Account Manager para que te aparezcan esta información.

<figure><img src=".gitbook/assets/Screen Shot 2022-09-22 at 10.42.21.png" alt=""><figcaption><p>Obtención de credenciales de dLocal</p></figcaption></figure>

{% hint style="info" %}
La información de tu procesador debes enviarla a [https://forms.gle/vuiaaBLRrUDCWJUb8](https://forms.gle/vuiaaBLRrUDCWJUb8)
{% endhint %}

### Stripe

Para obtener las credenciales, primero deben tener desactivado el modo prueba:

<figure><img src=".gitbook/assets/Screen Shot 2022-09-22 at 10.53.57.png" alt=""><figcaption></figcaption></figure>

Luego, deben ingresar al [dashboard de Stripe](https://dashboard.stripe.com/apikeys) y luego a la sección desarrolladores y por último a Claves de API (o directamente a [https://dashboard.stripe.com/apikeys](https://dashboard.stripe.com/apikeys)).&#x20;

<figure><img src=".gitbook/assets/Screen Shot 2022-09-22 at 10.46.56.png" alt=""><figcaption><p>Obtención de credenciales de Stripe</p></figcaption></figure>

Debe obtener tanto la **Clave publicable** como la **Clave Secreta**. Sugerimos que se genere una nueva clave secreta de la siguiente manera:

<figure><img src=".gitbook/assets/Screen Shot 2022-09-30 at 13.03.42.png" alt=""><figcaption><p>Click a Crear clave secreta</p></figcaption></figure>

Luego, ingrese el Nombre de la clave (Sugerencia: Preauth, para que luego sea fácil identificarla)&#x20;

<figure><img src=".gitbook/assets/Screen Shot 2022-09-30 at 13.04.41.png" alt=""><figcaption><p>Ingresar Nombre de la clave</p></figcaption></figure>

Por último, copie y pegue en el formulario de Preauth la clave secreta. No olvides enviar esta información vía [privnote](https://privnote.com/) para evitar cualquier filtración de datos.

<figure><img src=".gitbook/assets/Screen Shot 2022-09-30 at 13.07.18.png" alt=""><figcaption></figcaption></figure>

{% hint style="info" %}
La información de tu procesador debes enviarla a [https://forms.gle/vuiaaBLRrUDCWJUb8](https://forms.gle/vuiaaBLRrUDCWJUb8)
{% endhint %}

### Mercadopago

Es muy sencillo obtener las credenciales. Para esto deben ir a la [sección de Credenciales](https://www.mercadopago.com.pe/settings/account/credentials) (Tu negocio/Configuración/Credenciales)

<figure><img src=".gitbook/assets/Screen Shot 2022-09-22 at 11.00.32.png" alt=""><figcaption><p>Ir al a sección Credenciales</p></figcaption></figure>

A continuación, ingresas a Credenciales de producción

<figure><img src=".gitbook/assets/Screen Shot 2022-09-22 at 11.01.32.png" alt=""><figcaption><p>Ir a la sección Credenciales de producción</p></figcaption></figure>

Por último, en esta pantalla podrás ver las credenciales que necesitamos.

<figure><img src=".gitbook/assets/Screen Shot 2022-09-22 at 11.04.31.png" alt=""><figcaption><p>Credenciales de producción</p></figcaption></figure>

{% hint style="info" %}
La información de tu procesador debes enviarla a [https://forms.gle/vuiaaBLRrUDCWJUb8](https://forms.gle/vuiaaBLRrUDCWJUb8)
{% endhint %}

### Conekta

Para obtener las credenciales de conekta debes ingresar al panel administrativo desde: [https://panel.conekta.com/](https://panel.conekta.com/)

Luego, ingresas a la sección de desarrolladores para poder ingresar a "Consultar API Keys de producción"

<figure><img src=".gitbook/assets/image (1).png" alt=""><figcaption><p>Consultar API Keys de producción</p></figcaption></figure>

Por último, te aparecerá una ventana con tus credenciales, ojo que solo podrás obtenerlos una vez, la próxima tendrás que regenerarlos.

<figure><img src=".gitbook/assets/image.png" alt=""><figcaption><p>API Keys</p></figcaption></figure>

Por último, copia y pega en el formulario de Preauth la clave secreta. No olvides enviar esta información vía [privnote](https://privnote.com/) para evitar cualquier filtración de datos.

{% hint style="info" %}
La información de tu procesador debes enviarla a [https://forms.gle/vuiaaBLRrUDCWJUb8](https://forms.gle/vuiaaBLRrUDCWJUb8)
{% endhint %}
