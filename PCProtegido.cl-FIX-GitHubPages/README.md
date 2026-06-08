# PC Protegido.cl - Sitio Web para GitHub Pages

Sitio web estático listo para subir a GitHub y publicar en GitHub Pages.

## Archivos incluidos

- `index.html`: página principal del sitio.
- `assets/styles.css`: estilos responsivos.
- `assets/app.js`: menú móvil y formularios con WhatsApp.
- `assets/logo.svg`: logo editable en SVG.
- `assets/og-pc-protegido.svg`: imagen para vista previa del sitio.
- `.nojekyll`: archivo recomendado para GitHub Pages.

## Cómo subir a GitHub Pages

1. Crear un repositorio en GitHub, por ejemplo: `pc-protegido`.
2. Subir todos los archivos de esta carpeta al repositorio.
3. Entrar a **Settings > Pages**.
4. En **Build and deployment**, seleccionar:
   - Source: `Deploy from a branch`
   - Branch: `main`
   - Folder: `/root`
5. Guardar y esperar que GitHub genere el enlace público.

## Importante sobre formularios y WhatsApp

GitHub Pages es un hosting estático, por eso no puede enviar datos a una base de datos ni publicar automáticamente en un grupo de WhatsApp.

El sitio prepara el mensaje, lo copia al portapapeles y abre el grupo de WhatsApp para pegarlo y enviarlo. También incluye enlace directo al número +56 9 2173 3645 mediante `wa.me`.

## Datos configurados

- Empresa: PC Protegido.cl
- Correo: PcProtegido.cl@gmail.com
- WhatsApp directo: +56 9 2173 3645
- Grupo soporte general: https://chat.whatsapp.com/GygQDwCU1VKDwCBrHrIP0w?s=sw&p=i&ilr=1
- Grupo agente PC Protegido.cl: https://chat.whatsapp.com/Bqyp36i898x28mWocy4NpF?s=sw&p=i&ilr=1
- Grupo formulario de contacto: https://chat.whatsapp.com/F1AK1zsW9TlLWv2RzsPxVZ?s=sw&p=i&ilr=1

## Personalización rápida

Para cambiar precios o textos, editar directamente el archivo `index.html`.
Para cambiar colores, editar las variables al inicio de `assets/styles.css`.
