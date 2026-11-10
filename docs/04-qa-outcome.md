# QA Report — hub "Ingenieria para cuentas de fondeo"

- **Fecha:** 2026-11-10 · **Target:** http://127.0.0.1:4321 (preview Astro local, 5 paginas)
- **Modo:** Full · Tier Standard · Driver: $B (gstack headless Chromium 158) · Duracion ~15 min
- **Arbol:** limpio antes de QA · Branch: main (renombrado desde master) · Commit final: bc3a6f8

## Cobertura (5/5 paginas)
| Pagina | 200 | Consola | Copia-scan | Resultado |
|---|---|---|---|---|
| / | OK | 0 errores | 0 promesas | PASS |
| /ninjatrader/ | OK | 0 errores | 0 promesas | PASS |
| /ninjatrader/matriz/ | OK | 0 errores | 0 promesas | PASS |
| /ninjatrader/edge-report/ | OK | 0 errores | 0 promesas | PASS |
| /contacto/ | OK | 0 errores | 0 promesas | PASS |

## Top por severidad
1. **ISSUE-001 [Medium][Links]** — Footer linkea `https://poner-url-del-portfolio/` (dominio invalido) en las 5 paginas. Root cause: placeholder en `src/lib/site.ts` sin reemplazo. **FIXED (verified):** render condicionado en `src/layouts/Base.astro` (commit bc3a6f8); re-check browser OK (issue-001-after.jpg), consola sigue limpia. **Remainder:** fusionar el link de vuelta cuando exista la URL real del portfolio.
2. **ISSUE-002 [Low][Content]** — Typo "POR QUE EXISTS ESTO" en el kicker de la home. **DEFERRED** (tier Standard no incluye cosmetic) — arreglo de 1 palabra pendiente de autorizacion.

## Health Score
- PRE-fix: **98** (Links 85 por 1 destino roto; dedup por root cause)
- POST-fix: **100** — provisional: rendimiento (LCP/CLS) y accesibilidad NO medidos en este run

## Framework
Static Astro 5 (ningun marcador SPA/Next/Rails/WordPress). Ningun script runtime en paginas (consola героя por defecto).

## Limites (discovered)
- Checkpoint granularity: page-granular (adaptacion economica del strict per-probe checkpoint en sitio estatico)
- Rendimiento y accesibilidad no evaluados — pendientes para el run pre-cutover en *.pages.dev
