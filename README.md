# Emulador GBA para GitHub Pages

Emulador de Game Boy Advance en el navegador usando [EmulatorJS](https://emulatorjs.org) con el núcleo mGBA.

## Estructura

```
gba-emulator/
├── index.html        Página principal
├── .nojekyll         Evita que GitHub Pages procese la web con Jekyll
├── css/
│   └── style.css     Estilos
├── js/
│   ├── app.js        Biblioteca de juegos y arranque del emulador
│   └── pad.js        Controles táctiles, velocidad x2, tamaño de botones
└── roms/
    ├── games.json    Lista de juegos de la biblioteca
    └── (tus .gba / .zip)
```

## Añadir juegos

1. Copia el archivo a `roms/` (por ejemplo `roms/mi-juego.gba`).
2. Añádelo a `roms/games.json`:

```json
[
  { "id": "mi-juego", "title": "Mi juego", "file": "roms/mi-juego.gba" },
  { "id": "otro",     "title": "Otro juego", "file": "roms/otro.zip" }
]
```

- `id`: identificador corto, sin espacios. Sirve para enlaces directos: `https://TU-USUARIO.github.io/TU-REPO/?juego=mi-juego`
- `title`: nombre que aparece en el desplegable. Las partidas guardadas se asocian a este nombre, así que no lo cambies si no quieres perderlas.
- `file`: ruta relativa al archivo.

También se puede abrir cualquier `.gba` del ordenador con el selector de archivos, sin subirlo.

## Publicar en GitHub Pages

1. Sube el contenido de esta carpeta a tu repositorio.
2. En el repositorio: **Settings → Pages → Build and deployment → Source: Deploy from a branch**, rama `main`, carpeta `/ (root)`.
3. Tras un par de minutos estará en `https://TU-USUARIO.github.io/TU-REPO/`.

## Probar en local

`fetch()` no funciona abriendo el archivo con doble clic (`file://`). Usa un servidor local:

```bash
python -m http.server 8000
# y abre http://localhost:8000
```

## Notas

- GitHub rechaza archivos de más de 100 MB; los juegos de GBA ocupan como mucho 32 MB, así que no hay problema. Si pesan mucho, súbelos en `.zip`.
- El emulador se descarga del CDN de EmulatorJS, así que hace falta conexión a internet.
- Ten en cuenta que un repositorio público hace descargables los archivos de `roms/` para cualquiera.
