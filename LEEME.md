# Catálogo de inmuebles — guía de uso

Todo el sitio es **un solo archivo**: `index.html`. Se abre con doble clic en cualquier
computador, sin internet, para revisar cómo va quedando.

---

## Ya viene configurado

En el bloque **`2) CONFIGURACIÓN`** de `index.html` ya están tus datos:

```js
const CONFIG = {
  nombre:   "Giobeta Inmobiliaria",
  whatsapp: "573166172477",   // WhatsApp del agente
  telefono: "573182108002",   // línea para llamadas
  correo:   "",               // si pones un correo, aparece en el pie
  ciudad:   "Pasto, Nariño"
};
```

Solo cambia algo de aquí si te cambia un número. El correo está vacío a propósito:
si escribes uno entre las comillas, aparece solo en el pie de página.

---

## Cambiar los inmuebles

Más abajo está el bloque **`3) INMUEBLES`**. Cada inmueble es un bloque entre llaves:

```js
{
  id: "001",
  titulo: "Casa de dos pisos con patio",
  operacion: "venta",          // "venta" o "arriendo"
  tipo: "Casa",                // "Casa", "Apartamento", "Lote" o "Local"
  barrio: "Barrio Las Cuadras",
  precio: 320000000,           // solo números, sin puntos ni $
  area: 140,
  habitaciones: 3,
  banos: 2,
  parqueadero: 1,
  foto: "fotos/casa-cuadras.jpg",
  descripcion: "Texto que describe el inmueble."
},
```

**Para agregar uno:** copia un bloque completo (desde `{` hasta `},`), pégalo debajo
y cambia los datos. Dale un `id` distinto.

**Para quitar uno:** borra el bloque completo, incluida la coma final.

Reglas que no se pueden romper:

- El precio va **sin puntos y sin signo $**. El sitio le pone los puntos solo.
- Si el inmueble no tiene habitaciones o baños (un lote), escribe `0`.
- Si todavía no tienes foto, deja `foto: ""` y se muestra un dibujo gris en su lugar.
- Cada bloque termina en `},` — menos el último de la lista, que termina en `}`.

**Las fotos** van dentro de la carpeta `fotos/`. Nombres sin tildes ni espacios.
Tamaño recomendado: 1200 × 900 px y menos de 300 KB, para que cargue rápido en celular.

---

## Publicar en GitHub Pages — cinco pasos

### 1. Crea la cuenta

Entra a **github.com** → *Sign up*. Correo, contraseña y nombre de usuario.

> **Ojo con el nombre de usuario.** Queda dentro de la dirección para siempre.
> Sugerido: **`giobeta`** → la página quedaría en `giobeta.github.io/inmobiliaria`.
> Si ese usuario ya está ocupado, prueba `giobetapasto` o `giobetainmobiliaria`.
> Sin tildes, sin espacios, sin puntos.

### 2. Crea el repositorio

Botón **+** arriba a la derecha → *New repository*.

- **Repository name:** `inmobiliaria`
- Marca **Public**
- **No** marques "Add a README file"
- *Create repository*

### 3. Sube los archivos

En la página que aparece, haz clic en **uploading an existing file**.

Arrastra allí **el contenido** de esta carpeta: `index.html`, `robots.txt`,
`sitemap.xml`, `.nojekyll` y la carpeta `fotos`.

> Si `.nojekyll` no se ve en tu computador, activa "mostrar archivos ocultos".
> Si aun así no aparece, súbelo después o déjalo: el sitio funciona igual.

Abajo, botón verde **Commit changes**.

### 4. Enciende la página

Pestaña **Settings** (arriba) → menú izquierdo, **Pages**.

En *Source* elige **Deploy from a branch**; en *Branch* elige **main** y carpeta **/ (root)**.
**Save**.

Espera entre uno y tres minutos y recarga. Aparece un recuadro con tu dirección:

```
https://TUgiobeta.github.io/inmobiliaria/
```

Esa es la dirección definitiva. **Es la que va en el código QR.**

### 5. Ajusta la dirección en tres archivos

Ahora que ya la conoces, reemplaza `USUARIO` por tu usuario real en:

- `index.html` → líneas con `USUARIO.github.io` (son 4, en el bloque de arriba)
- `robots.txt` → una línea
- `sitemap.xml` → una línea

En GitHub puedes editar directo: abre el archivo → ícono del lápiz → cambias → *Commit changes*.

---

## Para cambiar algo después

Entra a tu repositorio → clic en `index.html` → ícono del **lápiz** → editas →
botón **Commit changes**. En dos minutos el sitio ya está actualizado.
No hay que volver a subir nada.

---

## Que Google la encuentre

1. Entra a **search.google.com/search-console**
2. *Agregar propiedad* → **Prefijo de URL** → pega tu dirección
3. Verifica con el método de **etiqueta HTML**: te da una línea `<meta ...>`
   que pegas en `index.html` justo debajo de `<head>`
4. Ya verificada, ve a *Sitemaps* y escribe `sitemap.xml` → *Enviar*

Google tarda entre unos días y dos semanas en mostrarla en los resultados.

---

## Si después compras el dominio propio

No hay que rehacer nada ni reimprimir tarjetas.

1. En GitHub: *Settings* → *Pages* → *Custom domain* → escribes `tuinmobiliaria.com` → *Save*
2. Donde compraste el dominio, creas estos registros DNS:
   - Cuatro registros **A** apuntando a `185.199.108.153`, `185.199.109.153`,
     `185.199.110.153` y `185.199.111.153`
   - Un registro **CNAME** para `www` apuntando a `TUUSUARIO.github.io`
3. De vuelta en GitHub, marca **Enforce HTTPS**

La dirección vieja sigue redirigiendo sola, así que **el QR impreso nunca deja de servir**.

---

## Problemas comunes

| Qué pasa | Por qué | Cómo se arregla |
|---|---|---|
| La página sale en blanco | Falta una coma o una llave en el bloque de inmuebles | Revisa que cada inmueble termine en `},` |
| Sale error 404 | El archivo no se llama exactamente `index.html` | Renómbralo, todo en minúscula |
| Las fotos no aparecen | La ruta no coincide con el nombre real | Revisa mayúsculas, tildes y la extensión (.jpg / .png) |
| El botón de WhatsApp no abre el chat | El número quedó mal | Debe ser `57` + 10 dígitos, sin espacios ni `+` |
| Los precios salen raros | Le pusiste puntos o `$` | El precio va solo con números |
