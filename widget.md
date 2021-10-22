---
description: Intégranos en tu página y disfruta de la magia.
---

# Widget

### Insertando SDK

Con el siguiente script te aseguras que nuestro SDK sea cargado en tu web. Puedes hacerles pequeños cambios, pero te recomendamos no hacerlo.

```javascript
 !function(e,t){window.PreauthObject=t,window[t]=window[t]||function(){(window[t].q=window[t].q||[]).push(arguments)};const n="script",o=document.createElement(n),c=document.getElementsByTagName(n)[0];o.async=1,o.src=e,c.parentNode.insertBefore(o,c)}("https://cdn.preauth.io/preauth.js","preauth");
```

### Configuración del SDK

El SDK necesita cierta información para su correcto funcionamiento, por lo que debes configurar el id de la orden y los callbacks que se ejecutaran en caso de éxito o fallo según corresponda. Puedes ver más detalle en la descripción del modelo [SDKConfiguration](widget.md#modelos).

```javascript
preauth("init", {
  order: "4085-whOdSyS2FkGmm4j9feJNeMh0SjQDgLa5xAUENBkajsfQK",
  onSuccess() {
    //CODE  
  },  
  onError(e) {
    //CODE
  }
});
```

### Mostrando widget

Para mostrar el widget solo necesitas enviar el texto **"start"** como se muestra a continuación:

```javascript
preauth("start");
```

### Ejemplo completo

```html
<!DOCTYPE html>
<html>
<head>
  <script type="text/javascript">
    !function(e,t){window.PreauthObject=t,window[t]=window[t]||function(){(window[t].q=window[t].q||[]).push(arguments)};const n="script",o=document.createElement(n),c=document.getElementsByTagName(n)[0];o.async=1,o.src=e,c.parentNode.insertBefore(o,c)}("https://cdn.preauth.io/preauth.js","preauth");

    preauth("init", {
      order: "4085-whOdSyS2FkGmm4j9feJNeMh0SjQDgLa5xAUENBkajsfQK",
      onSuccess() {
        //CODE  
      },  
      onError(e) {
        //CODE
      }
    });

    function openPreauth() {
      preauth("start");
    }
  </script>
</head>
<body>
  <button onclick="openPreauth">Click me!</button>
</body>
</html>
```

### Modelos

#### SDKConfiguration

| Attributo | Tipo     | Descripción                                                                                          | Ejemplo                                            |
| --------- | -------- | ---------------------------------------------------------------------------------------------------- | -------------------------------------------------- |
| order     | Texto    | Id de la orden, obtenido al crear la orden por medio del API REST.                                   | 4085-whOdSyS2FkGmm4j9feJNeMh0SjQDgLa5xAUENBkajsfQK |
| onSuccess | Callback | Callback que se ejecuta cuando la orden ha sido preautorizada correctamente.                         |                                                    |
| onError   | Callback | Callback que se ejecuta cuando ocurre algún error al preautorizar la orden. Ver modelo PreauthError. |                                                    |

#### PreauthError

| Attributo | Tipo             | Descripción                          | Ejemplo              |
| --------- | ---------------- | ------------------------------------ | -------------------- |
| code      | PreauthErrorCode | Código de error interno.             | 100                  |
| message   | Text             | Mensaje asociado al código de error. | Modal closed by user |

#### PreauthErrorCode

| Código | Descripción                                               |
| ------ | --------------------------------------------------------- |
| 100    | Cuando el widget es cerrado.                              |
| 101    | Cuando el widget no ha cargado correctamente.             |
| 102    | Cuando sucede algún error al realizar la preautorización. |
