# pet-capcutclub-preview — boceto de la landing de CapCut Club

Boceto de trabajo (boceto 1) de la landing de venta de **CapCut Club**, publicado solo para revisión.
No es la versión final: no tiene animaciones, las imágenes y los videos están pendientes y los textos pueden cambiar.

La landing real se trabaja en el repo [`pet-capcutclub`](https://github.com/davidprietooficial-ux/pet-capcutclub).

## URL y alojamiento

| Dato | Valor |
|---|---|
| URL del boceto | https://davidprietooficial-ux.github.io/pet-capcutclub-preview/ |
| Hosting | GitHub Pages, servido desde este repo |
| Rama publicada | `main`, carpeta raíz (`/`). Modo *Deploy from a branch* (sin workflow propio) |
| HTTPS | Forzado (*Enforce HTTPS* activo). Sin dominio propio (`cname` vacío) |
| Indexación | Bloqueada: `robots.txt` con `Disallow: /` y `<meta name="robots" content="noindex, nofollow, noarchive, nosnippet">` |

> La URL cambió el **2026-11-14** al renombrar el repo desde `capcut-club-preview`.
> La URL vieja (`.../capcut-club-preview/`) ya no funciona (devuelve 404): GitHub Pages no redirige. Si alguien tenía el enlace viejo, hay que mandarle el nuevo.

## Stack

- **Un solo archivo HTML estático** (`index.html`, ~290 KB). Sin framework, sin build, sin JavaScript (no hay ninguna etiqueta `<script>`).
- **CSS inline** en un bloque `<style>` con variables en `:root`.
- **Fuentes embebidas en base64** (WOFF2) con `@font-face`: *Special Gothic Expanded One* (titulares) e *Inter Tight* 400 y 600 (cuerpo). No se carga nada de Google Fonts ni de otro CDN.
- **Una imagen embebida en base64** (PNG del mockup de la caja del programa, en el hero).
- No hay `package.json`, dependencias, scripts ni workflows de GitHub Actions.
- Referencia de diseño anotada en el comentario inicial del `<style>`: arquitectura adaptada de una landing de referencia externa, con la identidad de Plan de Edición Total en tema claro.

## Estructura

```
pet-capcutclub-preview/
├── index.html   # Toda la página: estilos, fuentes e imagen embebidos
├── robots.txt   # Bloquea a todos los rastreadores (Disallow: /)
├── .nojekyll    # Archivo vacío: GitHub Pages sirve los archivos tal cual, sin Jekyll
└── README.md
```

## Cómo verlo en local

No hace falta instalar nada. Cualquiera de estas dos opciones:

```bash
# Opción 1: abrir el archivo directamente
open index.html

# Opción 2: servidor local (útil para probar en el celular dentro de la misma red)
python3 -m http.server 8000
# luego abrir http://localhost:8000
```

## Build

No hay build. Lo que está en `index.html` es exactamente lo que se publica.

## Despliegue

1. Editar `index.html` (o `robots.txt`).
2. Hacer commit en `main` y `git push origin main`.
3. GitHub Pages republica solo en uno o dos minutos. El estado se ve en la pestaña *Actions* del repo (despliegue automático de Pages) o en *Settings → Pages*.
4. Abrir la URL con recarga forzada para comprobar el cambio (GitHub Pages envía `cache-control: max-age=600`, es decir, puede tardar hasta 10 minutos en verse).

No hay que subir nada a Hostinger: este repo **no** se publica en `planediciontotal.com`.

## Secciones de la página

Cada sección está marcada en `index.html` con un comentario `<!-- ══ NN · Nombre ══ -->` (la barra fija va primero y no lleva número), en este orden:

| # | Sección | Notas |
|---|---|---|
| — | Barra fija de compra | Solo móvil y tableta (se oculta desde 1024 px) |
| 01 | Hero | Titular, CTAs y mockup de la caja |
| 02 | Banda de la oferta | Marquesina estática (sin animación) |
| 03 | Video + cifras | Video pendiente; cifras +2 M, +15, +1.000, +50 |
| 04 | El problema | 3 dolores |
| 05 | Qué vas a lograr | 3 resultados |
| 06 | CTA intermedio | |
| 07 | Temario (`#modulos`) | 6 módulos: 1–4 fundamentos, 5–6 CapCut |
| 08 | Bio | Foto pendiente |
| 09 | Antes y después | Videos pendientes |
| 10 | Testimonios | 4 tarjetas, videos pendientes |
| 11 | La oferta (`#oferta`) | Precio y botón de compra de Hotmart |
| 12 | Sellos | |
| 13 | Bonos | 3 bonos + aviso del bono de IA sin confirmar |
| 14 | FAQ | `<details>` nativos, sin JS |
| 15 | Cierre | |
| 16 | Pie | WhatsApp, legales, razón social, aviso de no afiliación a CapCut |

## Dónde se cambian los datos más editados

Todo está escrito directamente en `index.html`; no hay archivo de configuración. Conviene buscar el texto con el buscador del editor y cambiar **todas** sus apariciones. Ojo: algunas cifras aparecen también escritas en letras ("Diez meses" en la FAQ, "siete días" en el cierre), así que buscar solo el número no las encuentra.

| Dato | Valor actual | Dónde aparece |
|---|---|---|
| Precio | `23 USD` (antes `67`) | Barra fija, botón del hero, banda, CTA intermedio, oferta, FAQ, cierre |
| Duración del acceso | `10 meses` | Hero, banda, oferta (texto y lista), FAQ (como "Diez meses") |
| Garantía | `7 días` | Hero, banda, lista de la oferta, sellos, FAQ, cierre (como "siete días") |
| Enlace de compra (Hotmart) | `https://pay.hotmart.com/M107158341L?off=oynghv9l&checkoutMode=10&bid=1786761312497` | Solo el botón "Comprar ahora" de la sección 11. Los demás botones apuntan a `#oferta` |
| Medios de pago mostrados | `Visa · Mastercard · PayPal` | Oferta (sección 11) y FAQ |
| WhatsApp | Enlace `wa.me` y número visible | Pie (sección 16) |
| Razón social y año | `Mirai Group Co S.A.S.` · `2026` | Pie (sección 16) |
| Enlaces legales | `href="#"` (vacíos) | Pie (sección 16) |
| Colores y tipografías | Variables `--naranja`, `--texto`, `--display`, `--cuerpo`, etc. | Bloque `:root` al inicio del `<style>` |

## Tracking e integraciones

| Integración | Estado |
|---|---|
| Meta Pixel | No hay |
| GA4 / Google Tag Manager | No hay |
| Microsoft Clarity | No hay |
| Hotmart | Solo un enlace de checkout (producto `M107158341L`, oferta `oynghv9l`). Sin script ni widget |
| Formularios | No hay |
| WhatsApp | Enlace directo `wa.me` en el pie |

Es intencional que un boceto no tenga tracking. Si alguien compra desde el botón del boceto, la venta pasa por el checkout real de Hotmart.

## Seguridad

- Sitio 100 % estático, sin JavaScript ni formularios.
- GitHub Pages no permite configurar cabeceras HTTP (CSP, X-Frame-Options, etc.) ni usar `.htaccess`. No hay ninguna cabecera de seguridad configurada desde el repo; GitHub añade por su cuenta `strict-transport-security` y fuerza HTTPS.
- Los enlaces externos (Hotmart y WhatsApp) usan `target="_blank" rel="noopener noreferrer"`.
- El repo es público: no subir tokens, claves ni datos privados.

## Problemas conocidos

- **Falta la cabecera del documento.** El archivo empieza directamente en `<title>`: no tiene `<!doctype html>`, `<html lang="es">`, `<meta charset="utf-8">` ni `<meta name="viewport">`. Consecuencias: el navegador lo renderiza en modo *quirks* y, sobre todo, **en el celular se ve como versión de escritorio reducida** porque falta el viewport. Las tildes se ven bien en GitHub Pages porque el servidor envía `charset=utf-8` en la cabecera, pero al abrir el archivo en local (`open index.html`) podrían verse mal. Para revisar la versión móvil del boceto hay que añadir esas líneas al inicio.
- **Contenido de relleno**: video de presentación, foto de la bio, clips de antes/después, videos de testimonios y mockups de los bonos son marcadores grises con texto.
- **Bono de IA de 24 h**: el aviso de la sección 13 dice que el bloque "se enciende cambiando un valor", pero en este boceto no existe ese bloque ni ningún interruptor (no hay JS). Es solo un aviso para decidir si aplica.
- **Enlaces legales vacíos** (`href="#"`) en el pie.
- **Nombres de la bio y los testimonios** ("Juan" como mentor y cuatro nombres en testimonios): no se sabe si son reales o de relleno [por confirmar].
- **Garantía de 7 días**: el boceto la menciona en varias secciones. Comprobar si sigue vigente para CapCut Club antes de pasar textos a `pet-capcutclub` [por confirmar].
- **Peso**: ~290 KB en un solo archivo por las fuentes y la imagen en base64. Aceptable para un boceto; en la versión final conviene servirlas como archivos aparte.
- **Datos del producto por confirmar** en la versión final: precio, duración del acceso, bonos y enlace de Hotmart [por confirmar] (este boceto refleja lo que se tenía al hacerlo: único commit, del 15 de agosto de 2026).

## Repos relacionados

Todos en `github.com/davidprietooficial-ux`, con la convención `pet-<sitio>`.

| Repo | Sitio |
|---|---|
| [`pet-form-webinar`](https://github.com/davidprietooficial-ux/pet-form-webinar) | form-webinar.planediciontotal.com (Hostinger) |
| [`pet-clase`](https://github.com/davidprietooficial-ux/pet-clase) | clase.planediciontotal.com (Hostinger) |
| [`pet-plandedicion-venta`](https://github.com/davidprietooficial-ux/pet-plandedicion-venta) | pet-plandedicion-venta.vercel.app (Vercel) |
| [`pet-capcutclub`](https://github.com/davidprietooficial-ux/pet-capcutclub) | Landing real de CapCut Club (subdominio `capcutclub` en Hostinger [por confirmar]) |
| `pet-capcutclub-preview` | Este repo: boceto de revisión en GitHub Pages |
| `pet-workshopexclusivo` | workshopexclusivo.planediciontotal.com (Hostinger, privado) |

En Hostinger ningún subdominio está conectado a Git: los archivos se suben a mano (o con la API/MCP de Hostinger) a la carpeta del subdominio. Este repo es la excepción, porque se publica solo con GitHub Pages.
