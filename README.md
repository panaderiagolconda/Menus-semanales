# Menú del día — Golconda

Página web que muestra el menú del día de Golconda, optimizada para celular.
Detecta el día automáticamente, permite ver los demás días de la semana y tiene
un botón para pedir por WhatsApp. El menú se toma de un archivo de Excel
(`menu.xlsx`), así que **no hay que tocar código para cambiarlo cada semana**.

---

## Archivos del proyecto

Todos deben estar **juntos en la misma carpeta / repositorio**:

| Archivo | Para qué sirve | ¿Se edita? |
|---|---|---|
| `index.html` | La página web | Casi nunca (solo precios/teléfono) |
| `menu.xlsx` | El menú de la semana | **Sí, cada semana** |
| `logo.png` | El logo de Golconda | No |
| `AmsiProCond-Regular.woff2` | Tipografía de la marca | No |
| `AmsiProCond-Bold.woff2` | Tipografía de la marca | No |

---

## 1. Publicar la página por primera vez (GitHub Pages)

1. Entra a **github.com**, crea una cuenta (*Sign up*) o inicia sesión.
2. Arriba a la derecha: **+ → New repository**. Ponle un nombre en minúsculas
   (ej. `golconda-menu`), déjalo en **Public** y crea el repositorio.
3. **Add file → Upload files** y arrastra los **6 archivos** (los 5 de la tabla
   + este README). Abajo: **Commit changes**.
4. **Settings → Pages**. En *Source* elige **Deploy from a branch**; en *Branch*
   elige **main** y la carpeta **/ (root)**; clic en **Save**.
5. Espera 1–2 minutos y recarga esa página. Aparecerá:
   *"Your site is live at https://TUUSUARIO.github.io/golconda-menu/"*.
   Esa dirección es el **enlace que se pega en WhatsApp** cada semana. No cambia nunca.

---

## 2. Actualizar el menú cada semana

**No hay que borrar nada.** Subir el archivo con el mismo nombre lo reemplaza solo.

1. Abre `menu.xlsx` en Excel.
2. En la hoja **«Menú»** cambia las fechas y los platos. Un plato por fila.
3. Guarda (déjalo con el nombre **`menu.xlsx`**).
4. En GitHub: **Add file → Upload files**, arrastra el `menu.xlsx` nuevo y haz
   **Commit changes**. Al tener el mismo nombre, reemplaza el anterior automáticamente.
5. En 1–2 minutos la página se actualiza sola. Ábrela y haz un **refresco fuerte**
   (mantén *Shift* y recarga) para ver los cambios.

### Columnas del Excel

- **Día**: elígelo en la lista desplegable.
- **Fecha**: la fecha que se muestra (ej. `13 jul`). Repítela en todas las filas de ese día.
- **Festivo**: `Sí` solo si ese día cobra tarifa de domingo/festivo; si no, `No`.
- **Plato**: el nombre del plato.
- **Descripción**: nota corta que aparece **debajo** del plato (ej. *Con crema de leche y alcaparras*). Es **opcional**: si la dejas vacía, no se muestra nada.

> Regla de oro: no cambies los títulos de la fila 1 ni el nombre de la hoja «Menú».

---

## 3. Días con dos menús (como el sábado)

Solo en esos días, llena la columna **«Opción»** con `Opción 1` en las filas del
primer menú y `Opción 2` en las del segundo. La página mostrará sola un botón para
alternar entre las dos. Sirve para cualquier día; si el día tiene un solo menú,
deja «Opción» vacía.

---

## 4. Cambiar precios, teléfono o WhatsApp

Estos casi nunca cambian y **no** están en el Excel, sino en `index.html`.
Ábrelo y busca cerca del inicio el bloque `const CONFIG = {`:

- `whatsapp`: número en formato internacional, sin `+` ni espacios (ej. `573106516929`).
- `telefonos`: los que aparecen en el pie de página.
- `precios`: tarifas normales y de domingo/festivo.
- `tiquetera`, `adicionales`, `cambiosProteina`: los demás datos fijos.

Cambia solo el texto entre comillas. Guarda y sube el `index.html` a GitHub igual
que el Excel.

---

## 5. Si algo sale mal

- **La página muestra un menú viejo**: dale refresco fuerte (*Shift* + recargar).
  GitHub puede tardar 1–2 minutos en publicar el cambio.
- **No se ve el logo o la letra se ve genérica**: falta subir `logo.png` o los
  archivos `.woff2`. Deben estar en la misma carpeta que `index.html`.
- **La página se ve sin platos al abrir el archivo con doble clic**: es normal.
  Por seguridad, el navegador solo lee el Excel cuando la página está publicada
  (en el enlace de GitHub Pages), no al abrir el archivo local.
- **El Excel no se pudo leer**: la página tiene un menú de respaldo dentro del
  código para no quedar en blanco. Revisa que el `menu.xlsx` conserve los títulos
  de columna y el nombre de hoja «Menú».

---

## Nota: editar desde Google Sheets (opción futura)

Se puede migrar el menú a una Google Sheet para editarlo en línea (incluso desde
el celular) sin subir nada a GitHub. Tiene una ventaja de comodidad, pero también
un detalle técnico de compatibilidad que hay que probar. Si se quiere ese camino,
se ajusta el `index.html` para leer la hoja publicada. Ver la conversación del
proyecto para los pros y contras.
