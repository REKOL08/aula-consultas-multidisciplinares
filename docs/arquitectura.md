# Arquitectura

HTML/CSS/JavaScript con ES Modules sin dependencias, compilación o backend. `index.html`: formularios; `style.css`: diseño responsive; `core.js`: rutas, validación, enlaces y progreso; `app.js`: eventos, render y persistencia; `ayuda.html`: documentación visible en el sitio.

Estado versión 1: `{version:1,discipline,question,evidence,checks:boolean[6],sources:[{id,title,author,year,url,notes}]}`. Clave localStorage `aula-consultas-v1`. Límites: 4000 caracteres consigna; 16000 desarrollo; 200 fuentes; ID 100, título 300, autor 200, fecha 10, URL 2000, notas 4000. Importación máxima 2 MB. Identificadores únicos, área enumerada y booleanos estrictos. Se reconstruyen solo campos admitidos antes de reemplazar datos. Campos textuales se escapan al renderizar; URLs admiten solo http(s), sin credenciales. Propiedades adicionales se descartan.

El guardado captura fallos localStorage y muestra aviso; el trabajo permanece en memoria y puede exportarse. Una lectura inválida inicia estado vacío sin eliminar deliberadamente la clave, aunque un cambio posterior la reemplazará. Exportar descarga JSON con Blob; importar usa File.text y JSON.parse.

Las rutas son constantes específicas por disciplina. No hay análisis de lenguaje, IA ni validación semántica. La búsqueda usa encodeURIComponent y enlaces externos; no ejecuta peticiones desde la app a esos buscadores. El progreso es proporción de casillas manualmente marcadas.

Sin service worker, cuentas, sincronización, API, notificaciones o procesamiento remoto. Se necesita conexión para la primera carga.
