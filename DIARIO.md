# DIARIO — barberia-puerto-web

## 20/07/2026 — Dominio propio para Raúl: precio acordado, pendiente de compra y migración

**Contexto**: la web vive en `labarberiadelpuerto.cuxy.app` (subdominio de Cuxy). Oscar le ofrece a Raúl la opción de tener su propio dominio (`barberiadelpuerto.es`, ~16€/año) para que, si la relación con Cuxy termina en algún momento, él conserve el dominio de su web y de su app.

**Precio acordado** (aplica también como plantilla para futuros clientes de CitaBot/MenuWeb en el mismo caso):
- **50€ pago único** por la gestión inicial: registrar el dominio y configurarlo (DNS, apuntar la web y lo que haga falta).
- **50€ cada 3 años** en concepto de "gestión y renovación de dominio" — cubre el coste real (3 × 16€/año ≈ 48€) más un margen mínimo. No se plantea como partida de beneficio: el beneficio de esta relación viene de la mensualidad (30€/mes), el dominio solo tiene que no dar pérdidas. Evitar en el contrato justificarlo como "el dominio vale más dinero" (no es cierto y es comprobable por el cliente) — mejor "gestión y renovación de dominio: 50€/3 años", más honesto y sin flancos.
- Redactar esta cláusula en la plantilla de contrato de `cuxy-empresa/4-contratos/` cuando se confirme con Raúl.

**Pendiente**: Oscar va a comprar `barberiadelpuerto.es`. Una vez comprado, migrar la web desde `labarberiadelpuerto.cuxy.app` a la URL propia (Cloudflare Pages: añadir dominio personalizado, actualizar DNS, redirigir la URL antigua) y revisar si `citabotapp-barberia-puerto` o `barberia-puerto-api` referencian la URL vieja en algún sitio (recordatorios WhatsApp, enlaces, etc.).

**Titularidad**: se registra con los datos de Oscar (no de Raúl) — idea propia de Oscar, no comentada aún con el cliente. Si en el futuro hay que traspasarlo de verdad a Raúl (o a quien él decida), el camino es la **"Transmisión de dominio" de Red.es** (`www.dominios.es`, no Namecheap): se solicita desde ahí con los datos del nuevo titular, este confirma por email (`plandedominios@red.es`), resolución en 1-3 días laborables. Puede pedir certificado digital (DNIe) de alguna de las partes — comprobar eso cuando llegue el momento. La opción "Change Ownership" de Namecheap NO sirve para esto en `.es` (solo mueve la cuenta que gestiona el dominio, obliga a mantener los contactos actuales).

---

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

## 09/07/2026 — Rediseño web completo + dominio + prueba reserva

- Nav eliminada (nombre y teléfono ya están en hero e info)
- Hero: logo de Raúl (PNG 1024x1024, fondo #000 exacto), ancho hasta 680px, sin recuadro visible
- Formulario de reserva: `<input type="date">` reemplazado por **calendario inline** en CSS/JS puro — muestra el mes actual, hoy seleccionado por defecto con slots ya cargados, domingos y días pasados deshabilitados, navegación con flechas
- Calendario compacto (celdas 34px) para no desproporcionarse respecto al resto del formulario
- **Dominio personalizado**: `labarberiadelpuerto.cuxy.app` activo en Cloudflare Workers
- **Prueba real**: reserva hecha desde la web → cita apareció en tiempo real en la app de Raúl (Expo Go)

**Pendiente:**
- Fotos reales del local cuando Raúl las proporcione
