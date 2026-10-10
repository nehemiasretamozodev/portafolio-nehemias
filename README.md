# Portafolio Nehemias — estilo currículum web

Proyecto SvelteKit inspirado en un diseño de currículum minimalista (no es código copiado del sitio de referencia).

## Ejecutar en Visual Studio Code

1. Instala Node.js LTS si aún no lo tienes.
2. Abre la carpeta de este proyecto en Visual Studio Code.
3. En Terminal ejecuta:

```bash
npm install
npm run dev
```

4. Abre http://localhost:5173

## Personalización

- Edita `src/routes/+page.svelte` para modificar los datos, proyectos, fechas y experiencia.
- El correo configurado es `nehemiasretamozo@icloud.com` (se corrigió la coma de tu mensaje por un punto).
- El teléfono configurado es `+51 910064458`.
- Hay un recuadro con iniciales **NR** como reemplazo de fotografía: no se puso una foto inventada.
- Los proyectos son ejemplos basados en trabajos mencionados, sin URLs públicas hasta que las confirmes.
- **Ctrl + K** abre la paleta de comandos; también puedes hacer clic en la barra inferior.
- Para añadir una foto propia, colócala en `static/foto-perfil.jpg` y cambia el elemento `.portrait` por `<img class="portrait" src="/foto-perfil.jpg" alt="Fotografía de Nehemias" />`, agregando `object-fit:cover` a su CSS.

## Publicación futura

Cuando el proyecto esté terminado, puedes subirlo a GitHub y conectarlo con Vercel. Antes de configurar un dominio canónico, sitemap y Search Console, define la dirección definitiva que usará tu página.

## Nota

Confirma y completa la experiencia laboral y formación académica antes de publicarlo. No se han inventado empresas, títulos ni años de experiencia.
