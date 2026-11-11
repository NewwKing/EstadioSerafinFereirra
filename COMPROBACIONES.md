# Comprobaciones de entrega · V3.1

## Resultado: 36 pruebas automáticas superadas

Ejecutadas con `node --test tests/*.test.js`. Cubren la identidad del proyecto, las cinco estaciones originales, las cuatro parejas de mascota/escudo, integridad y rutas de los 25 GLB, los 11 JPG nuevos, hashes del manifiesto, las dos filas posteriores (6 + 5), el contador combinado de 15 escudos, la compactación de mallas y la conservación de la galería original.

También cubren el reproductor de audio, reproducción/pausa, pausa por visibilidad, invalidación de respuestas tardías, límites de volumen/posición, preferencias persistidas y almacenamiento bloqueado.

Sintaxis: todos los módulos `src/*.js` pasaron `node --check`; `run.py` y `preparar_offline.py` pasaron `py_compile`.

## Recursos añadidos

Se añadieron 11 GLB corregidos y 11 JPG asociados. Los GLB se guardan en `models/club-*.glb`; las imágenes se guardan en `assets/clubs/*.jpg`. Se verificaron sus cabeceras GLB 2.0, longitud declarada y ausencia de dependencias externas. Los JPG se optimizaron para su uso en la ficha lateral.

Los 11 escudos se colocan detrás de la fila original: seis en Z = -10.5 y cinco en Z = -19.5. Los GLB se cargan durante el arranque con tres tareas simultáneas. La compactación estática agrupa geometrías por material y atributos para reducir llamadas de dibujo, manteniendo materiales y orientación recibida. No se asignan nuevas mascotas.

## Servidor HTTP

Se ejecutó `python run.py --no-browser --port 8765` y se recibieron respuestas HTTP 200 con MIME correcto para `index.html`, los módulos JavaScript, imágenes JPG y modelos GLB. Se verificaron rutas de muestra de ambas filas.

## Límites de verificación

No se pudo ejecutar la escena Three.js completa en un navegador con acceso al CDN en este entorno. Por tanto, la posición visual final, el encuadre real de las dos filas, el rendimiento FPS y la interacción física con los 11 pedestales deben revisarse en el navegador del usuario. Las pruebas automáticas validan estructura, archivos, rutas, configuración e integración del código, pero no sustituyen esa comprobación visual.

Las fichas nuevas muestran el nombre y la imagen JPG de cada club. Las reseñas históricas se dejaron como pendientes de confirmación; no se inventaron fechas de fundación, títulos ni datos deportivos.

## Revisión en tu navegador

1. Descomprime la carpeta completa y ejecuta `python run.py`.
2. Espera a que termine la carga de los 11 modelos adicionales.
3. Entra en Cancha Media y pulsa **V** para revisar la vista general de las tres filas.
4. Camina hacia atrás, pasando la fila original. Los 11 escudos nuevos deben verse en dos filas: seis y cinco.
5. Acércate a un escudo nuevo, míralo y pulsa **E**. Debe abrirse la ficha lateral con su JPG y nombre; **E**, **Esc** o × la cierran.
6. Comprueba que las cuatro vitrinas originales siguen funcionando con E y que las cinco estaciones, las teclas 1–5, la música, HQ/LQ y la postal siguen disponibles.
7. El contador debe mostrar **0/15** en una instalación limpia y guardar los descubrimientos localmente.

El ZIP original recibido no se sobrescribió. Esta entrega es una copia V3.1 ampliada; los archivos originales de la web se conservaron y sólo se añadieron las nuevas filas, sus recursos y la lógica asociada.
