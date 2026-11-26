# MORELA Esthetic — web

Web de la clínica estética de Paula Pastor (Vila-real - Castellón). Dominio: https://www.morelaestetica.com

## Stack
- HTML + CSS + JS vanilla. **Sin build, sin npm, sin framework.** Cada página lleva su CSS y JS inline.
- Fuentes: Google Fonts (Cormorant Garamond + DM Sans).
- Supabase JS por CDN solo para el formulario de newsletter (tabla `suscriptores`).
- Paleta en `:root` de cada página: `--cream --beige --rose --dark --gold --gold-light`.

## Estructura
```
index.html                 Home (hero, sobre mí, servicios en acordeón, galería, reseñas, contacto)
blog/index.html            Índice del blog
blog/*.html                Artículos (3)
aviso-legal.html
politica-privacidad.html   Incluye la política de cookies (#cookies)
robots.txt / sitemap.xml   SEO — añadir al sitemap cada página nueva
googlec7cc2a79253ac666.html  Verificación de Google Search Console. NO BORRAR.
*.jpg / *.jpeg / *.mp4     Imágenes y vídeos, todos en la raíz
```

## Imágenes y vídeos
- Todo en la **raíz** del repo (no hay carpeta `assets/`).
- Desde `index.html` y las páginas legales: ruta relativa sin carpeta → `src="fotopaula.jpeg"`.
- Desde `blog/*.html`: `src="../cejaschica.jpeg"`.
- `og:image` y JSON-LD usan URL absoluta: `https://www.morelaestetica.com/<archivo>`.
- Al añadir fotos: nombre sin espacios ni ñ, JPG de máx. ~900–1200 px de ancho, y en el HTML poner `width`/`height` y `loading="lazy"`.
- Hay originales y vídeos subidos que la web no usa (p. ej. `undiaconpaula.mp4`, `antesmicroblanding.jpeg`); se guardan como material.

## Despliegue
- Vercel, enlazado a GitHub (`marcdaniclaramonte-jpg/morela-web`). No hay que ejecutar nada.
- Push a `main` → **producción** (www.morelaestetica.com). `morelaestetica.com` redirige 308 al www.
- Push a cualquier otra rama o PR → **preview** en
  `https://morela-web-git-<rama>-marcdaniclaramonte-jpgs-projects.vercel.app`
  (protegida: hay que tener sesión iniciada en Vercel para verla).

## Variables de entorno
Ninguna es necesaria: no hay build ni backend propio. La config de Supabase está escrita en `index.html` a propósito:
- `SUPABASE_URL`
- `SUPABASE_PUBLISHABLE_KEY` (clave pública; la tabla tiene RLS que solo permite INSERT al rol anon)

Nunca poner en el repo la `service_role` / secret key de Supabase ni crear `.env` con secretos (están en `.gitignore`).

## Datos del negocio
- WhatsApp/teléfono Paula: 641 579 467 (`https://wa.me/34641579467`)
- Email: beautymorela@gmail.com
- Dirección: Passatge Josep Pasqual Goterris Albiol, 12 (bajo), 12540 Vila-real (Castellón)

## Notas
- Tras cambios gordos, recordar Ctrl+F5 / incógnito: la caché suele mostrar la versión vieja.
- `aquabrush.html` y `producto-hero.png` (si aparecen en la carpeta) son de otro proyecto: no subir a este repo.
