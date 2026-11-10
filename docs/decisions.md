# Decisiones del proyecto

Todas las decisiones tomadas durante las sesiones de office-hours, eng review, CEO review, ship y design review.

## Decisiones de arquitectura (D14-D22, AUQ)

### D14 — Secuenciación del widget de evidencia en fase 1
- **Skill:** /plan-eng-review
- **Pregunta:** ¿Cómo resolvemos la inconsistencia de secuenciación del widget de evidencia?
- **Respuesta:** A — Fase 1 publica con evidencia estática fechada; el widget vivo llega en fase 3
- **Rationale:** la fase 1 mantiene su promesa de "publica en días" sin romper dependencias; la captura con fecha es honesta
- **Aplicado en:** doc Recommended Approach fase 1 enmendada

### D15 — Defensa estadística del Edge Report
- **Skill:** /plan-eng-review
- **Pregunta:** ¿Qué exigimos al formato Edge Report para no publicar un número curve-fitted?
- **Respuesta:** A — OOS/walk-forward obligatorio + muestra mínima + etiquetado in/out-of-sample
- **Rationale:** validación out-of-sample es el estándar mínimo para hablar de "ventaja estadística"
- **Aplicado en:** edge-report.astro (estado: "sin validación, la tabla queda vacía")

### D16 — Frescura de la matriz de compliance
- **Skill:** /plan-eng-review
- **Pregunta:** ¿Cómo evitamos que la matriz envejece?
- **Respuesta:** A — Filas fechadas con fuente visible, re-verificación trimestral, disclaimer
- **Rationale:** una fila fechada con fuente convierte "verdad desactualizable" en "verdad con fecha de vencimiento visible"
- **Aplicado en:** matriz.astro (cada fila con "verificado: fecha + URL de fuente")

### D17 — Recepción y atribución de WhatsApp
- **Skill:** /plan-eng-review
- **Pregunta:** ¿Definimos la recepción de WhatsApp o el CTA queda como link simple?
- **Respuesta:** A — wa.me con mensaje pre-llenado que marca el origen + plantilla de intake
- **Rationale:** el criterio "inbound del sitio" se vuelve medible; la plantilla pre-califica
- **Aplicado en:** src/lib/site.ts (WA_TEXT con intake) + contacto.astro

### D18 — Contrato de datos del feed VPS
- **Skill:** /plan-eng-review
- **Pregunta:** ¿Qué exporta exactamente el feed del VPS y cómo se enmarca el drawdown propio?
- **Respuesta:** A — Métricas agregadas anonimizadas (%, sin identificadores) + nota fija de enmarcado
- **Rationale:** cero exposición sensible; tu drawdown público se convierte en demostración del Protocolo
- **Aplicado en:** doc Recommended Approach fase 3

### D19 — Upgrade de gstack
- **Skill:** /gstack-upgrade
- **Pregunta:** ¿Actualizar gstack v1.97 → v1.98?
- **Respuesta:** A — Sí, actualizar
- **Rationale:** proceso no-destructivo (rescue ref), refresca todos los skills instalados
- **Resultado:** checkout v1.98.0.0, install global re-registrado, tooling completo

### D20 — Arquitectura del sitio: rebuild en código
- **Skill:** /plan-ceo-review (triggered por pregunta directa del usuario)
- **Pregunta:** ¿Dónde construimos louiscalderon.dev: código+Cloudflare, subdominio paralelo, o seguimos en Framer?
- **Respuesta:** A — Rebuild completo en código (GitHub → Cloudflare Pages/Workers)
- **Rationale:** el diseño exige piezas data-driven en código; tu contenido es pequeño (migración barata); te ahorras la suscripción; preview→cutover con cero downtime
- **Aplicado en:** repo Astro creado, wrangler.jsonc, Cloudflare Workers deploy

### D21 — Alcance del rebuild: hub-solo + portfolio aparte
- **Skill:** /plan-ceo-review
- **Pregunta:** ¿Qué contiene el rebuild: solo el hub o también el contenido actual?
- **Respuesta:** A — Hub-solo en el dominio; el portfolio general vive en su URL Framer aparte (proyectos.louiscalderon.dev)
- **Rationale:** patrón single-focus de competidores del nicho + instrucción del fundador ("quiero enfocar mis servicios en ello") + audiencias con estéticas opuestas (prior learning [landing-warm-local-direction])
- **Aplicado en:** site.ts PORTFOLIO_URL = proyectos.louiscalderon.dev; footer link condicional

### D22 — Crear repo GitHub público
- **Skill:** /ship
- **Pregunta:** ¿Creo el repo en GitHub desde aquí y con qué visibilidad?
- **Respuesta:** A — Crear PÚBLICO + push
- **Rationale:** código público ES evidencia de portafolio de developer; repo sin secretos verificado
- **Resultado:** https://github.com/louisCalderon888/louiscalderon-dev creado y pusheado

## Decisiones de arquitectura registradas vía gstack-decision-log

1. **CEO review (decisión única):** hub-solo en louiscalderon.dev, portfolio general queda en Framer URL aparte
   - Rationale: patrón single-focus de competidores + instrucción del fundador + audiencias con estéticas opuestas
   - Confidence: 9

2. **Ship primera publicación:** repo público louiscalderon-dev creado via gh, push main
   - Rationale: código público como evidencia de portafolio; repo sin secretos verificado
   - Confidence: 9

3. **Cutover:** louiscalderon.dev ahora sirve el hub en Cloudflare Workers (verificado: 200, wa.me real, 0 errores, CF-Cache HIT)
   - Rationale: finalización del pipeline office-hours → diseño → eng review → QA → ship → cutover
   - Confidence: 10

## Decisiones de premisas (office-hours)

### Premisa 1R (revisada)
El cliente QUIERE su cuenta fondata operando (demanda). Se VENDE la ingeniería que maximiza la probabilidad: sistema + validación + instalación + gestión de riesgo con límites definidos y drawdown negociado ANTES de la venta. El sitio vende ingeniería y muestra evidencia; nunca promete resultado.

### Premisa 2R (revisada)
Evidencia con dos roles: operativa propia en VPS como motor de evidencia continua + el caso del cliente ($2,000, verificado y con consentimiento escrito) como prueba social de tercero.

### Premisas 3-6
3. "Ventaja estadística" requiere UN número medible antes de usarse en marketing.
4. La compatibilidad por fondeo es producto, no letra pequeña.
5. "Programar estrategias" es la línea más commodity: degradarla y elevar validación/riesgo/operativa.
6. No hacer nada = clientes solo por WhatsApp, sin proceso, sin poder de precio.

## Open Questions resueltas

| OQ | Pregunta | Resolución |
|---|---|---|
| OQ1 | ¿Qué firms usan los clientes? | RESUELTA: MyFundedFutures, Lucid, e8, Apex (+ TakeProfitTrader). Three-tier offer aplicada |
| OQ2 | ¿Consentimiento del cliente? | RESUELTA: cliente aprobó. Caso $2,000 se publica anonimizado |
| OQ6 | ¿Pipeline de despliegue? | RESUELTA: GitHub → Cloudflare Workers (D20) |

## Open Questions pendientes

| OQ | Pregunta | Estado |
|---|---|---|
| OQ3 | ¿Hay backtests documentados listos para el primer Edge Report? | Pendiente: requiere walk-forward/OOS (días de cómputo) |
| OQ4 | Precios de los 3 paquetes | Pendiente: decisión del fundador |
| OQ5 | Tesis a 3 años | Pendiente: solo el fundador puede articularla |
| OQ7 | ¿Se espeja el bot de MFFU hacia Apex/TPT/e8? | Pendiente: decisión de arquitectura del servicio para el caso del cliente |
