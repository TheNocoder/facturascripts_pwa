FacturaScripts as PWA
=====================

Modificaciones mínimas necesarias para que FacturaScripts funcione como Aplicación Web Progresiva o PWA.

Para que una Web tradicional funcione como PWA se requiere como mínimo:

- Unos meta tags en el código HTML
- Un service-worker.js
- Un manifest.json
- Unas líneas de código JavaSctipt para cargar service-worker.js

Por lo tanto en FacturaScripts necesitaremos modificar las plantillas HTML para incluir los meta tags y el código JavaScript y añadir los los archivos de este repositorio.

Estas modificaciones sirven para convertir cualquier Web en PWA, solo tenéis que cambiar el nombre de la PWA y los iconos.

## Modificación HTML en FacturaScripts

Hay que añadir las siguientes meta etiquetas a HEAD para todos las páginas HTML:

```html
<meta name="viewport" content="width=device-width, initial-scale=1">
<meta name="mobile-web-app-capable" content="yes">
<meta name="application-name" content="FacturaScripts">
<meta name="apple-mobile-web-app-title" content="FacturaScripts">
<meta name="apple-mobile-web-app-capable" content="yes">
<link rel="manifest" href="/pwa/manifest.json">
```

Al final de BODY hay que añadir las siguientes líneas JavaScript para todas las páginas HTML, este código carga service-worker.js

```html
<script>
    window.addEventListener('load', function() {
        if ('serviceWorker' in navigator) {
            serviceWorkerReg = navigator.serviceWorker.register('/service-worker.js');
        } else {
            serviceWorkerReg = false;
        }
    });
</script>
```

El archivo index.example.html de este repositorio contiene un ejemplo con las modificaciones.

## Añadir archivos necesarios

Lor archivos necesarios y la estructura de directorio de los archivos es la siguiente:

    FacturaScripts/
        ├─ service-worker.js
        ├─ offline.html
        ├─ pwa/
           ├─ manifest.json
           ├─ icons/
              ├─ 16.png
              ├─ 32.png
              ├─ 64.png
              ├─ 120.png
              ├─ 180.png
              ├─ 192.png
              ├─ 512.png
              ├─ 512-maskable.png

Este repositorio mantiene esta estructura.

## Certificado SSL

Si estáis ejecutando FacturaScripts en "localhost" no es necesario certificado SSL, pero desde un dominio en Internet, no funcionará si no tenéis un certificado SSL.

## Probando... probando...

Simplemente copiando este repositorio a vuestro "localhost" y renombrando index.example.html a index.html podeis probar si se instala con PWA en http://localhost/

## License

MIT License
