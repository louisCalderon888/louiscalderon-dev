# Design Audit — louiscalderon.dev

Fecha: 2026-11-10 · Target: LIVE en producción · 5 páginas · Clasificador: PERSUADE

## Lidado inicial (First Impression)
- El sitio comunica **precisión y potencia equilibria** en tono cálido.
- Destaca la estructura en cards con la paleta tierra/verde — lectura fácil con fondo claro.
- Lo primero que registra el ojo: (1) H1 con Georgia 51px, (2) botones WhatsApp verde, (3) las dos cards de evidencia.
- Palabra única: **confiable**.

## Sistema de diseño extraído
- **Fuentes:** Georgia (display, serif cálido) + system-ui (body) — 2 familias.
- **Color:** paleta crema/terracota + verde WhatsApp como acción primaria. Coherente.
- **Headings:** H1 51px / H2 33.6px / H3 17.6px → re-escalado del h3 a ~19px.
- **Spacing:** escala de 8px coherente.
- **Touch targets:** corregidos (nav a display:inline-block + padding 12px + h 44px).

## Hallazgos arregla­dos (verified: 6 · bajo commit…)
1. FINDING-001: tokens unificados en :root — todos los colores literales eliminados (commit 671b767, 53cafb1). **LINT: 24 → 0 blocks.**
2. FINDING-002: :focus-visible ring visible para tecla (671b767).
3. FINDING-003+7+13: blanco puro en .btn → --wa-ink tinted; --surface #fffdf9; --th-bg; .callout con tokens (671b767).
4. FINDING-004+11: flechas pegadas a CTAs removidas; H1 con espacio para lectores (8557d36).
5. FINDING-008+09: skip-link + aria-current añadidos a Base (671b767).
6. FINDING-012: H2/H3 peso reducido a 600 para contraste de jerarquía (671b767). H3 17.6→19.2px.
7. ISSUE-002 de QA: typo "exists" → "existe" en kicker home (2652bb1).

## Pendientes (deferred — requieren contenido no creado)
- Footer: enlaces a privacidad y terminos — necesitas crear esos templates en Framer y luego aquí (2 min).
- OG image: no existe — needed para compartir el link con tarjeta visual.
- Skip: movimientos de animación — opcional, site es digno sin eso.

## Score
- Baseline: DN/A (primer passo) → **A- design · B+ AI-slop** post-fix
- Lint del craft: 24 blocks → 0 blocks · 20 asks restantes (mayormente filtros de formato)
