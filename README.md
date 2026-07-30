# Menú del día — Golconda

Sitio web del menú del día de Golconda, optimizado para celular. Tiene **dos
puntos de venta**: al abrir el enlace, el cliente elige primero el punto y luego
ve el menú de ese punto. El menú de cada punto se toma de su propio archivo de
Excel, así que **no hay que tocar código para cambiarlo cada semana**.

- **Santa Ana 109** — Cl. 109 # 6-55
- **Lisboa 134** — Cl. 134 # 9A-88

---

## Cómo funciona

- `index.html` es la **página de inicio**: muestra los dos puntos para elegir.
- Al elegir uno, lleva a `menu.html?p=santaana` o `menu.html?p=lisboa`.
- `menu.html` es **la misma página de menú para ambos puntos**; sabe cuál mostrar
  por el final del enlace (`?p=...`) y carga el Excel de ese punto.
- El enlace que se comparte por WhatsApp es el de **`index.html`** (la página de
  inicio); desde ahí el cliente escoge.

---

## Archivos del proyecto

Todos deben estar **juntos en la misma carpeta / repositorio**:

| Archivo | Para qué sirve | ¿Se edita? |
|---|---|---|
| `index.html` | Página de inicio (elegir punto) | No |
| `menu.html` | Página de menú (para ambos puntos) | Casi nunca (precios/datos de punto) |
| `menu-santaana.xlsx` | Menú de **Santa Ana 109** | **Sí, cada semana** |
| `menu-lisboa.xlsx` | Menú de **Lisboa 134** | **Sí, cada semana** |
| `logo.png` | Logo de Golconda | No |
| `AmsiProCond-Regular.woff2` | Tipografía de la marca | No |
| `AmsiProCond-Bold.woff2` | Tipografía de la marca | No |

---

## 1. Publicar por primera vez (GitHub Pages)

1. En **github.com**, crea el repositorio (Public) y **sube los 7 archivos**
   (todos juntos, en la raíz).
2. **Settings → Pages**. En *Source*: **Deploy from a branch**; *Branch*: **main**
   y carpeta **/ (root)**; **Save**.
3. Espera 1–2 minutos y recarga. Aparece *"Your site is live at https://TUUSUARIO.github.io/..."*.
   Ese es el enlace que se comparte con los clientes (lleva a la página de inicio).

---

## 2. Actualizar el menú cada semana

Cada punto tiene su **propio Excel**. **No hay que borrar nada**: subir el archivo
con el mismo nombre lo reemplaza solo.

1. Abre el Excel del punto: `menu-santaana.xlsx` o `menu-lisboa.xlsx`.
2. En la hoja **«Menú»** cambia las fechas y los platos. Un plato por fila.
3. Guarda **con el mismo nombre**.
4. En GitHub: **Add file → Upload files**, arrastra el Excel y **Commit changes**.
5. En 1–2 minutos la página se actualiza sola (refresco fuerte: *Shift* + recargar).

> Si el menú es igual en los dos puntos, hay que actualizar los dos Excel. Si
> siempre van a ser iguales, se puede configurar para que ambos usen un solo
> archivo — pídelo y se ajusta en un minuto.

### Columnas del Excel

- **Día**: en la lista desplegable.
- **Fecha**: la que se muestra (ej. `13 jul`). Repítela en las filas de ese día.
- **Festivo**: `Sí` solo si cobra tarifa de domingo/festivo; si no, `No`.
- **Plato**: el nombre del plato.
- **Descripción**: nota corta que aparece **debajo** del plato (opcional).

### Días con dos menús (como el sábado)

Llena la columna **«Opción»** con `Opción 1` y `Opción 2`. La página muestra sola
un botón para alternar. Si el día tiene un solo menú, deja «Opción» vacía.

---

## 3. Cambiar datos de un punto (dirección, teléfonos, WhatsApp) o precios

Estos casi nunca cambian y están en `menu.html`, cerca del inicio:

- Bloque **`const PUNTOS`**: nombre, dirección, teléfonos, WhatsApp y archivo de
  cada punto. (Ej.: si un punto tiene otro WhatsApp, cámbialo aquí.)
- Bloque **`const CONFIG`**: precios, tiquetera, adicionales y proteínas
  (compartidos por ambos puntos).

Cambia solo el texto entre comillas, guarda y sube `menu.html` a GitHub.

> Nota: los teléfonos de **Lisboa 134** se tomaron del arte de la marca y conviene
> confirmarlos; también revisa si Lisboa tiene un WhatsApp propio distinto.

---

## 4. Si algo sale mal

- **Menú viejo al recargar**: refresco fuerte (*Shift* + recargar); GitHub tarda 1–2 min.
- **No se ve el logo o la letra se ve genérica**: falta subir `logo.png` o las
  fuentes `.woff2` (deben estar junto a los HTML).
- **Sin platos al abrir el archivo con doble clic**: es normal; el navegador solo
  lee el Excel cuando la página está **publicada** (enlace de GitHub Pages).
- **El Excel no se pudo leer**: la página tiene un menú de respaldo interno para no
  quedar en blanco. Revisa que el Excel conserve los títulos de columna y la hoja «Menú».
