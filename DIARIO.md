# DIARIO — barberia-puerto-web

## 08/07/2026 — Creación del proyecto

Web pública de reservas para La Barberia del Puerto (Raúl Giménez, Burriana).

**Funcionalidad:**
- Información del negocio: dirección, teléfono, horario
- Google Maps embed (Avinguda Mediterrània, 27, Burriana)
- Formulario de reserva online:
  - Nombre + teléfono
  - Servicios (dropdown dinámico desde `GET /servicios` de barberia-puerto-api)
  - Fecha (picker con mínimo = hoy)
  - Hora (slots dinámicos desde `GET /disponibilidad?fecha=X`, se actualiza al cambiar fecha)
  - Submit → `POST /citas-web` → cita aparece en app en tiempo real
- Política de privacidad: cuxy.app/privacidad

**Diseño:** tema negro/dorado, coherente con el logo de Raúl.

**Deploy:** Cloudflare Pages
- Repo: cuxycuxy/barberia-puerto-web (público)
- Workers & Pages → Create → Connect to Git → barberia-puerto-web → rama main → sin build command → directorio raíz /

**Pendiente:**
- Conectar a Cloudflare Pages (Oscar)
- Añadir dominio personalizado si Raúl tiene uno
- Fotos reales del local cuando Raúl las proporcione
