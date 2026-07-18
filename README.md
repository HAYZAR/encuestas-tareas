# Encuestas sobre tareas escolares — IED Los Rosales

Sitio estático (GitHub Pages) que recoge respuestas **anónimas** de docentes, familias y estudiantes y las guarda en una **Google Sheet** mediante Google Apps Script.

Archivos:
- `index.html` — el sitio completo (una sola página, sin dependencias que instalar).
- `Code.gs` — el backend de Google Apps Script.

---

## Paso 1 · Crear la hoja de cálculo
1. Crea una Google Sheet nueva (por ejemplo, **“Encuestas Tareas 2026”**).
2. No necesitas crear pestañas: el script creará **Docentes**, **Familias** y **Estudiantes** automáticamente en la primera respuesta.

## Paso 2 · Publicar el backend (Apps Script)
1. En la hoja: menú **Extensiones ▸ Apps Script**.
2. Borra el contenido y pega todo el archivo `Code.gs`. Guarda (💾).
3. **Implementar ▸ Nueva implementación ▸** tipo **Aplicación web**:
   - **Ejecutar como:** Yo.
   - **Quién tiene acceso:** Cualquier usuario.
4. Autoriza los permisos cuando lo pida.
5. Copia la **URL** que termina en `/exec`.

## Paso 3 · Conectar el sitio
1. Abre `index.html` y busca, cerca del inicio del `<script>`, el bloque:
   ```js
   const CONFIG = { SCRIPT_URL: "PEGA_AQUI_TU_URL_DE_APPS_SCRIPT" };
   ```
2. Reemplaza el texto por tu URL `/exec`. Guarda.

> Mientras no configures la URL, el sitio funciona en **modo demostración**: muestra la pantalla de éxito pero no guarda nada (útil para probar el diseño).

## Paso 4 · Publicar en GitHub Pages
1. Sube `index.html` a tu repositorio (por ejemplo `hayzar.github.io/encuestas-tareas/`).
2. En **Settings ▸ Pages**, activa GitHub Pages sobre la rama `main`.
3. Tu sitio quedará en una URL como `https://hayzar.github.io/encuestas-tareas/`.

---

## Enlaces directos por público
Puedes compartir un enlace específico para cada audiencia usando el `#`:

| Público      | Enlace                                   |
|--------------|------------------------------------------|
| Docentes     | `…/encuestas-tareas/#docentes`           |
| Familias     | `…/encuestas-tareas/#familias`           |
| Estudiantes  | `…/encuestas-tareas/#estudiantes`        |

El enlace sin `#` muestra la pantalla de bienvenida con las tres opciones (ideal para un solo QR general).

---

## Notas
- **Anonimato:** el sitio no pide nombre, correo ni identificador. Solo registra fecha/hora en el servidor.
- **Un registro por envío:** cada “Enviar respuestas” agrega una fila. La pantalla final ofrece “Enviar otra respuesta” para dispositivos compartidos (una tablet en el aula, por ejemplo).
- **Columnas dinámicas:** si más adelante agregas o cambias preguntas, el script crea las columnas nuevas sin dañar las existentes.
- **Si ves un error al enviar:** confirma que la implementación de Apps Script tiene acceso “Cualquier usuario” y que pegaste la URL que termina en `/exec` (no la de `/dev`).
