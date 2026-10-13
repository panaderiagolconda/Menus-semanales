# Golconda — Sitio de temporada (Halloween 2026)

Versión especial del sitio de Golconda para fechas de temporada. Mantiene el
**menú del día** de los dos puntos de venta y agrega una página de
**productos de temporada** (ahora Halloween; después se reutiliza para Navidad).

- **Santa Ana 109** — Cl. 109 # 6-55
- **Lisboa 134** — Cl. 134 # 9A-88

---

## Cómo se organizan los dos desarrollos

Todo vive en **el mismo repositorio**, en dos **ramas** (*branches*). Una rama
es una copia completa de los archivos, independiente de la otra:

| Rama | Qué contiene | Cuándo se usa |
|---|---|---|
| `main` | El sitio normal: solo los menús del día | Todo el año (vuelve en noviembre) |
| `temporada` | El sitio de temporada: menús + Halloween (luego Navidad) | Octubre, diciembre… |

GitHub Pages publica **una sola rama a la vez**. Cambiar de desarrollo es
escoger qué rama se publica. **El enlace que tienen los clientes no cambia.**

---

## Archivos de la rama `temporada`

Todos van **juntos en la raíz** de la rama (sin carpetas):

| Archivo | Para qué sirve | ¿Se edita? |
|---|---|---|
| `index.html` | Inicio de temporada: elegir punto de venta + acceso a Halloween | No |
| `temporada.html` | Página de productos de temporada y "Arma tu pedido" | Rara vez (precios, textos) |
| `menu.html` | Menú del día, con un aviso que lleva a Halloween | Casi nunca |
| `menu-santaana.xlsx` | Menú de Santa Ana 109 | **Sí, cada semana** |
| `menu-lisboa.xlsx` | Menú de Lisboa 134 | **Sí, cada semana** |
| `logo.png` | Logo normal (lo usa `menu.html`) | No |
| `logo-halloween.png` | Logo claro para el fondo oscuro | No |
| `halloween-caja.jpg` | Foto de la caja de galletas | No |
| `halloween-kit.jpg` | Foto del kit para decorar | No |
| `halloween-pieza-caja.jpg` | Pieza completa de la caja (sección "Compártelo") | No |
| `halloween-pieza-kit.jpg` | Pieza completa del kit (sección "Compártelo") | No |
| `AmsiProCond-Regular.woff2` | Tipografía de la marca | No |
| `AmsiProCond-Bold.woff2` | Tipografía de la marca | No |

> `logo.png`, los dos Excel y las fuentes **ya están en `main`**. Al crear la
> rama `temporada` a partir de `main` se copian solos; no hay que subirlos.

---

## 1. Montar la rama `temporada` (solo la primera vez)

### a) Crear la rama
1. Entra al repositorio en **github.com**.
2. Arriba a la izquierda, sobre la lista de archivos, haz clic en el botón que
   dice **`main`** (el selector de ramas).
3. Escribe `temporada` y haz clic en **Create branch temporada from main**.
4. Ahora el selector dice **`temporada`**: todo lo que subas se guarda en esa rama.

### b) Subir los archivos nuevos
1. **Verifica que el selector diga `temporada`** (no `main`).
2. **Add file → Upload files**.
3. Arrastra estos 8 archivos del paquete:
   `index.html`, `menu.html`, `temporada.html`, `logo-halloween.png`,
   `halloween-caja.jpg`, `halloween-kit.jpg`, `halloween-pieza-caja.jpg`,
   `halloween-pieza-kit.jpg`.
4. `index.html` y `menu.html` **reemplazan** a los de esta rama (en `main` no
   se tocan).
5. Abajo, deja marcado **Commit directly to the `temporada` branch** y haz
   clic en **Commit changes**.

---

## 2. Cambiar entre desarrollos

| Quiero… | Pasos |
|---|---|
| **Activar la temporada** | **Settings → Pages** → en *Branch* elige **`temporada`** y carpeta **/ (root)** → **Save** |
| **Volver a solo menús** (noviembre) | **Settings → Pages** → en *Branch* elige **`main`** → **Save** |

En 1–2 minutos el enlace de siempre muestra la versión elegida. Para verla de
inmediato en el celular, recarga la página (o ábrela en una pestaña de incógnito).

> **Antes de volver a `main` en noviembre:** sube a `main` los Excel de la
> semana en curso. Mientras la temporada estuvo activa, los menús se
> actualizaron en `temporada`, así que los Excel de `main` estarán viejos.

---

## 3. Actualizar el menú semanal **durante la temporada**

Igual que siempre, pero **en la rama que esté publicada**:

1. En el repositorio, cambia el selector de ramas a **`temporada`**.
2. **Add file → Upload files**, arrastra `menu-santaana.xlsx` y/o
   `menu-lisboa.xlsx` (mismo nombre de siempre).
3. **Commit changes** (directo a `temporada`).

> Regla fácil: **el Excel se sube a la rama que está en Settings → Pages.**
> Si lo subes a la otra, la página no cambia.

---

## 4. Cambiar precios, domicilio o textos de temporada

Todo está al inicio del código de **`temporada.html`**, en el bloque marcado
**ZONA EDITABLE**. Cambia solo lo que está entre comillas o los números:

- **`const PRODUCTOS`**: nombre, precio (sin puntos: `25000`), textos, etiquetas
  y foto de cada producto.
- **`const PUNTOS`**: nombre, dirección y teléfonos de cada punto.
- **`const WHATSAPP`**: número que recibe los pedidos (`57` + número, sin espacios).
- **`const DOMICILIO`**: valor del envío (`3500`). Si el cliente elige
  *Recoger en el punto*, no se cobra.

Para editar en GitHub: abre `temporada.html` (con la rama `temporada`
seleccionada) → ícono del lápiz → cambia → **Commit changes**.

> Los precios que muestra la tarjeta de Halloween en la página de **inicio**
> (`$25.000` y `$42.000`) están escritos en `index.html`. Si cambias un precio,
> cámbialo en los dos archivos.

---

## 5. Cómo funciona el pedido

En `temporada.html` el cliente:
1. Suma cantidades con **+ / −** en cada producto.
2. En **Arma tu pedido** elige el **punto de venta** y si **recoge** o pide **domicilio**.
3. Ve el resumen y el total (con $3.500 de domicilio si aplica).
4. El botón verde abre WhatsApp con el pedido escrito: productos, domicilio,
   total, punto y forma de entrega.

---

## 6. Después de Halloween

- La cuenta regresiva ("Faltan X noches…") se oculta sola después del 31 de octubre.
- En noviembre basta con **volver a publicar `main`** (sección 2). La rama
  `temporada` queda guardada para la siguiente temporada.

## 7. Para Navidad

Se reutiliza la rama `temporada`: se reemplazan las fotos, los textos de
`temporada.html` y el ambiente decorativo (luna, murciélagos y fantasma por
nieve y luces, por ejemplo). Los menús siguen funcionando igual. Pide el ajuste
con las piezas de Navidad y se prepara el paquete.

---

## 8. Si algo sale mal

- **Sigue apareciendo la versión anterior**: espera 2 minutos y recarga; revisa
  en **Settings → Pages** qué rama quedó seleccionada.
- **Subí el Excel y el menú no cambió**: probablemente lo subiste a la rama que
  no está publicada. Revisa el selector de ramas y súbelo a la correcta.
- **No se ven fotos o el logo**: falta algún archivo en la rama `temporada`, o
  quedó dentro de una carpeta. Deben estar todos en la raíz.
- **La letra se ve distinta**: si faltan los `.woff2`, la página usa una letra
  de respaldo parecida. No se rompe nada.

---

## Pendiente por confirmar

- **Teléfono de Santa Ana 109.** Aparecen tres números distintos: 612 4076
  (pieza de la caja), 601 519 6681 (pieza del kit) y 601 519 6661 (menú). Por
  ahora se usa **601 519 6661**. Se corrige en `const PUNTOS` de
  `temporada.html` y de `menu.html`.
- **Logo claro.** `logo-halloween.png` se recortó de la pieza de la caja. Si
  tienen el logo oficial en color crema con fondo transparente, súbanlo con ese
  mismo nombre.
