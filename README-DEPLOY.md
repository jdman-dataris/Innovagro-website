# INNOVAGRO — Landing page · Guía de publicación

Sitio 100% estático: HTML + CSS/JS embebidos + assets. **No hay build, no hay dependencias, no hay backend.**
Se publica copiando esta carpeta tal cual a cualquier hosting estático (Netlify, Vercel, GitHub Pages, S3+CloudFront, cPanel, Nginx/Apache).

## Estructura
```
index.html        ← página principal (CSS y JS inline; único archivo grande)
privacidad.html   ← aviso de privacidad (LFPDPPP), enlazado desde footer y formulario
terminos.html     ← términos y condiciones, enlazado desde footer
robots.txt        ← permite indexar la home; excluye páginas legales
sitemap.xml       ← una sola URL
assets/           ← logos SVG de marca, favicon, og-image.jpg (1200×630)
assets/aliados/   ← logos FIRA, UNPCA, Sumagro, Salado Vega (franja "Confían en los líderes")
assets/func/      ← imágenes de producto en WebP (optimizadas)
assets/int/       ← logos de integraciones (CNH, QGIS, Case IH, John Deere, Ag Leader, Sveaverken)
```

## Dominio
Todo el SEO asume **https://inovagro.mx/** (el dominio lleva UNA sola "n" — es correcto, no "innovagro"):
- `<link rel="canonical">`, `og:url`, `og:image` y `twitter:image` en `index.html`
- `Sitemap:` en `robots.txt` y `<loc>` en `sitemap.xml`

Si se publica en otro dominio/subdominio, buscar y reemplazar `https://inovagro.mx/` en esos 3 archivos.

## DNS (si usan Netlify)
- Registro A de `inovagro.mx` → `75.2.60.5`
- CNAME de `www` → `<sitio>.netlify.app`
- HTTPS automático vía Let's Encrypt al propagar.

## Decisiones ya tomadas (no "arreglar")
- **Formulario de demo → `mailto:jsalado@inovagro.mx`**: es intencional, aprobado por el dueño. No conectar a backend salvo que se pida.
- **Newsletter**: hoy solo limpia el campo y muestra un alert de gracias (placeholder). Conectar a un servicio real es opcional/futuro.
- Copy y datos de contacto son finales: José Juan Salado Vega · jsalado@inovagro.mx · +52 229 929 9850 · WhatsApp wa.me/522299299850.
- Tipografías por Google Fonts (Inter + Outfit): requiere internet, es correcto así.

## Notas técnicas
- Interacciones (reveal on scroll, glow del cursor, tilt 3D, parallax, contadores, marquees) viven en el `<script>` al final de `index.html` — JS vanilla, sin librerías.
- Hay fallback `<noscript>` para que el contenido sea visible sin JavaScript.
- `backdrop-filter` (glassmorphism) degrada aceptablemente en navegadores sin soporte (fondos rgba sobre página clara).
- Peso total del sitio: ~630 KB.

## Checklist post-publicación
1. Abrir https://inovagro.mx/ y verificar HTTPS.
2. Probar el formulario (debe abrir el cliente de correo con los datos precargados).
3. Probar el botón de WhatsApp.
4. Compartir la URL en WhatsApp/redes y confirmar que aparece la og-image (validador: opengraph.xyz).
5. Enviar el sitemap en Google Search Console.
