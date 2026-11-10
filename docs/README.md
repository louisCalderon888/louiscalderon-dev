# Ingeniería para cuentas de fondeo — Documentación del proyecto

Este directorio contiene TODA la documentación generada durante el ciclo de vida del proyecto, desde el diagnóstico inicial hasta el sitio en producción. Cada archivo traza su origen (skill de gstack que lo generó, fecha, sesión).

## Índice

### Diseño y planeación
| Archivo | Origen | Fecha | Contenido |
|---|---|---|---|
| `01-design-doc.md` | `/office-hours` + `/plan-eng-review` | 2026-11-08 | Documento de diseño completo: problema, evidencia de demanda, premisas, segunda opinión, enfoque B (hub de 3 piezas), ledger de decisiones del eng review, reporte terminal GSTACK REVIEW REPORT |
| `02-eng-review-test-plan.md` | `/plan-eng-review` | 2026-11-08 | Plan de pruebas: páginas afectadas, interacciones a verificar, edge cases, critical paths con value cards |
| `sketches/sketch-oferta.html` | `/office-hours` (visual-design) | 2026-11-09 | Boceto HTML de la página de oferta (fase 1) — la jerarquía aprobada |
| `sketches/sketch-oferta.png` | browse.exe render | 2026-11-09 | Render del boceto |

### QA
| Archivo | Origen | Fecha | Contenido |
|---|---|---|---|
| `03-qa-report.md` | `/qa` | 2026-11-10 | Reporte QA: 5/5 páginas 200, 0 errores consola, scan copy 0 promesas, ISSUE-001 (footer placeholder) fixed, ISSUE-002 (typo) deferred, health 98→100 |
| `03-qa-baseline.json` | `/qa` | 2026-11-10 | Baseline para regresiones futuras |
| `04-qa-outcome.md` | `/qa` | 2026-11-10 | Outcome copiado al project dir de gstack |

### Design review
| Archivo | Origen | Fecha | Contenido |
|---|---|---|---|
| `05-design-audit.md` | `/design-review` | 2026-11-10 | Audit visual: first impression, sistema de diseño extraído, 7 hallazgos arreglados (tokens, focus-visible, touch targets, CTAs, skip-link, aria-current, escala H3), score A- design / B+ AI-slop |
| `05-design-baseline.json` | `/design-review` | 2026-11-10 | Baseline de design audit para regresiones |

### Decisiones y memoria de gstack
| Archivo | Origen | Contenido |
|---|---|---|
| `decisions.md` | compilado de sesión | Todas las decisiones D14-D22 + decisiones de arquitectura con rationale |
| `learnings-raw.txt` | `gstack-learnings-search` | 6 learnings: 2 arquitectura (cutover, tiers), 3 operacionales (git-bash, browse sandbox, bun crash), 1 tool (bin scripts con bun) |
| `question-log.jsonl` | `gstack-question-log` | Log de cada pregunta AUQ con respuesta del usuario |
| `builder-profile-louiscalderon-dev.jsonl` | `gstack-builder-profile` | Entradas de sesión para este proyecto |
| `analytics-eureka.jsonl` | gstack analytics | Momentos eureka registrados |
| `analytics-skill-usage.jsonl` | gstack analytics | Uso de skills por sesión |
| `analytics-spec-review.jsonl` | gstack analytics | Métricas de spec review |
| `gstack-config.yaml` | gstack config | Configuración activa de gstack |
| `gstack-installs.tsv` | gstack installs | Registro de instalación |

### Screenshots (evidencia visual)
| Archivo | Origen | Contenido |
|---|---|---|
| `screenshots/qa-initial.jpg` | `/qa` Phase 3 | Home inicial |
| `screenshots/qa-oferta.jpg` | `/qa` Phase 4 | Página de oferta |
| `screenshots/qa-matriz.jpg` | `/qa` Phase 4 | Matriz de compliance |
| `screenshots/qa-issue-001-after.jpg` | `/qa` Phase 8d | Recheck del fix del footer |
| `screenshots/design-first-impression.jpg` | `/design-review` Phase 1 | Primera impresión |
| `screenshots/design-after-state.jpg` | `/design-review` Phase 9 | Estado post-fix |

## Timeline del proyecto

```
2026-11-08  /office-hours        →  diagnóstico + diseño aprobado
2026-11-08  /plan-eng-review     →  5 hallazgos resueltos, CLEAR
2026-11-09  gstack upgrade       →  v1.97 → v1.98 (tooling completo)
2026-11-09  scaffold Astro        →  5 páginas, two-tier offer
2026-11-10  /qa                  →  2 issues → fixed, health 100
2026-11-10  /ship                →  repo GitHub público, Cloudflare Workers
2026-11-10  cutover              →  louiscalderon.dev sirve el hub
2026-11-10  T3 verificación      →  matriz con reglas oficiales, three tiers
2026-11-10  /design-review       →  7 fixes de craft, lint 24→0 blocks
2026-11-10  consolidación docs   →  este directorio
```

## Estado actual del sitio

- **URL:** https://louiscalderon.dev (Cloudflare Workers, edge cache HIT)
- **Repo:** https://github.com/louisCalderon888/louiscalderon-dev (público)
- **Portfolio general:** https://proyectos.louiscalderon.dev (Framer)
- **WhatsApp:** wa.me/573133678887 (con intake pre-llenado)
- **Health score:** 100 (QA + design review completos)
- **Lint craft:** 0 blocks, 20 asks (formato)

## Pendientes abiertos

1. **OQ3:** walk-forward/OOS del sistema insignia → primer Edge Report con número real
2. **OQ4:** precios de los 3 paquetes
3. **OQ5:** tesis a 3 años del fundador
4. **OQ7:** espejo manual del bot entre cuentas del cliente
5. **Privacy/terms:** crear páginas y linkearlas en el footer
6. **OG image:** para preview cards al compartir el link
