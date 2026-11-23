# Prompts para Claude — Diagramas Check-in 1 (4SA Grupo 4)
## Instrucciones generales
- **No insertar los diagramas en los DOCX.** Solo generar PNG 300 DPI transparentes, estilo UAE.
- Paleta: primario #A85C1E (terracota), texto #1A1A1A, fondo #FFF8F0 / #FFFFFF, gris #5A5A5A.
- Fuente: Aptos (o Inter/Calibri si Aptos no disponible). Títulos 10-11pt bold color #A85C1E, cuerpo 7-8pt.
- Tamaño: ancho 15-16 cm (para caber en columna 2.54 cm márgenes), alto proporcional, bordes redondeados 6px, sombra suave.
- Exportar como `fig_<nombre>.png` y guardar en `check-ins/CHK1_2026-11-01/` junto al DOCX. Luego insertar manualmente en Word (Insertar > Imagen, centrado, 4500000 EMU de ancho) manteniendo el caption existente `Figura 1. ... — elaboración propia a partir de Vallejo Lozado (2026).`
- Cada check-in lleva **exactamente 1 figura** (validado). No agregar figuras extra.

---

### 1. VERA YAGUAL — `fig_etapas` / `fig_organizacion` (Figura 1)
**Archivo destino:** `CHK1_4SA_G4_VERA_YAGUAL.pdf` — Figura 1. Organización caso de estudio — Finca Stefanny (6 ha, La Troncal) y problema de registro manual

**Prompt para Claude:**
```
Genera un diagrama sintético PNG 300 DPI (16 cm ancho, fondo #FFF8F0, borde #A85C1E 1.5px, radio 8px) titulado "Finca Stefanny — 6 ha (6 lotes ~1 ha) · La Troncal, La Virgilia" con dos bloques:

Bloque Izquierdo (60% ancho) — "Organización 6 ha":
- Grilla 3x2 de 6 parcelas etiquetadas L1 a L6, cada una "1.0 ha · suelo/estado fenológico/fecha siembra" (ícono hoja), color relleno #FFF8F0 con borde #A85C1E, etiqueta superior "Total 6 ha".
- Debajo, fila de 3 chips: "Ubicación: La Virgilia, La Troncal (Guayas)" + "Usuarios: 1 Admin con login" + "Trabajadores: sin login (contacto/asignaciones)".

Bloque Derecho (40% ancho) — "Problema: registro manual en libretas":
- Ícono libreta tachada + lista con 5 bullets compactos (7pt): 1) Pérdida/duplicidad sin respaldo, 2) Planificación verbal → tareas erradas, 3) Sin trazabilidad insumos por lote, 4) Sin reportes a tiempo, 5) Brecha seguridad/LOPDP (sin RBAC/hash/consentimiento).
- Nota al pie en 6pt italic #5A5A5A: "Elaboración propia a partir de Vallejo Lozado (2026) — 7 etapas arado→siembra→riego→fertilización→plagas→monitoreo→cosecha".

Estilo minimalista, sin fotos, sin copiar diagramas de tesis. Entregar PNG con nombre fig_organizacion.png
```

**Caption que se mantiene en el DOCX:** `Figura 1. Organización caso de estudio — Finca Stefanny (6 ha, La Troncal) y problema de registro manual — elaboración propia a partir de Vallejo Lozado (2026).`

---

### 2. PAZMIÑO RAIMUNDY — `fig_ranking` (Figura 1)
**Archivo destino:** `CHK1_4SA_G4_PAZMINO_RAIMUNDY.pdf` — Figura 1. Ranking C1–C7 (7 tesis) — Vallejo #1

**Prompt para Claude:**
```
Genera un gráfico de barras horizontales PNG 300 DPI (16 cm ancho) titulado "Ranking de factibilidad CIA — C1–C7 (0–10) · 7 tesis (11 PDFs)".

Datos (de mayor a menor):
- Vallejo Caña Stefanny: 9.2 (#1)
- González Maíz: 8.8 (#2)
- Otros 5: entre 5.0 y 7.5 (etiquetar genérico "T3 7.5", "T4 7.0", "T5 6.5", "T6 5.8", "T7 5.0" — no inventar títulos reales).
Barra Vallejo en #A85C1E sólido con borde, resto en #E8D9C8.

Incluye:
- Subfila debajo del título en 7pt #5A5A5A: "C1 Proceso 7 etapas | C2 12 Entidades | C3 Stack PHP/MySQL | C4 BPMN 0 | C5 Seguridad 0 hash | C6 LOPDP 1 cita | C7 Esfuerzo 7–10 días".
- Etiquetas de valor al extremo de cada barra (9.2, 8.8...).
- Nota pie 6pt italic: "Elaboración propia — 11 PDF verificados (HTTP 200/file) 17 MB · 18-oct-2026 · Vallejo vacíos perfectos: 0 BPMN, 0 hash/bcrypt, 1 cita LOPDP sin desarrollo".
- Leyenda pequeña: "Ventaja Vallejo: BPMN 10.0, esfuerzo 9.5, claridad proceso 9.5".

Estilo limpio, eje X 0–10, sin 3D. Exportar como fig_ranking.png
```

**Caption que se mantiene:** `Figura 1. Ranking C1–C7 (7 tesis) — Vallejo #1 — elaboración propia.`

---

### 3. AYOVI MINA — `fig_bpmn_asis_ayovi` (Figura 1) — BPMN AS-IS
**Archivo destino:** `CHK1_4SA_G4_AYOVI_MINA.pdf` — Figura 1. BPMN AS-IS 7 etapas con carriles

**Prompt para Claude:**
```
Genera un diagrama BPMN 2.0 AS-IS PNG 300 DPI (16 cm ancho, fondo blanco, swimlanes horizontales) titulado "BPMN AS-IS — Finca Stefanny — 7 etapas (arado a cosecha) — flujo manual 'libreta'".

Estructura:
- Pool "Finca Stefanny — Proceso Caña" con 2 lanes:
  LANE 1 (superior, #FFF8F0): "Administrador (único con login)" — contiene 7 tareas rectangulares en secuencia horizontal: T1 Arado/Preparación → T2 Siembra → T3 Riego → T4 Fertilización → T5 Control plagas/malezas → T6 Monitoreo → T7 Cosecha/Registro producción. Cada tarea con ícono libreta pequeño y etiqueta "asignación: actividad+lote+empleado+insumos".
  LANE 2 (inferior, #FFFFFF con trama gris clara): "Empleado agrícola (sin login — solo contacto/asignaciones)" — vacío de tareas con sistema, solo nota centrada en italic #5A5A5A: "Participa en proceso físico, sin interacción con sistema — BRECHA RBAC".

Elementos BPMN:
- Evento inicio (círculo verde) antes de T1, evento fin (círculo rojo grueso) después de T7.
- Flechas de secuencia negras entre tareas, todas lineales (sin compuertas BPMN, proceso narrado p.25-27 sin compuertas).
- Anotación (artefacto dotted) al pie: "Fuente parafraseada: Vallejo Lozado (2026) pp.25-27 y p.51 — Narrativa sin BPMN, 1 rol anon., sin Gherkin/INVEST".
- Leyenda pequeña abajo: cuadrado = tarea, círculo = evento, lane = rol. Nota: "Versión borrador PNG para CHK1; versión normativa .bpmn Bizagi/draw.io en Entrega 1 (29-nov-2026)".

Colores: borde tareas #A85C1E, texto #1A1A1A, lanes con cabecera #A85C1E texto blanco. Exportar como fig_bpmn_asis_ayovi.png
```

**Caption que se mantiene:** `Figura 1. BPMN AS-IS 7 etapas con carriles — elaboración propia a partir de Vallejo (2026).`

---

### 4. PARRALES FRANCO — `fig_rf_prioridad` (Figura 1)
**Archivo destino:** `CHK1_4SA_G4_PARRALES_FRANCO.pdf` — Figura 1. 18 RF por prioridad (89% Alta) y criterios Gherkin

**Prompt para Claude:**
```
Genera un diagrama combinado PNG 300 DPI (16 cm ancho) titulado "18 RF — Distribución por prioridad y criterios Gherkin/INVEST".

Parte superior (50% alto) — Donut + barras:
- Donut central 60/40: 89% (16 RF) Alta en #A85C1E, 11% (2 RF) Media en #E8D9C8. Etiquetas dentro: "16 Alta" y "2 Media". Centro del donut: "18 RF".
- Leyenda a la derecha en 7pt: Alta (89%) = núcleo operativo (auth hash/RBAC, lotes, insumos, asignaciones, producción/cosecha, reportes cifrados), Media (11%) = dashboard gráficos/filtros.

Parte inferior (50% alto) — Tabla mini 2 filas ejemplo Gherkin:
- Fila 1: "RF-07 Lotes — Must — Dado lote sin sembrar, Cuando asigno siembra, Entonces queda trazable por lote (INVEST: Pequeña, Testeable)".
- Fila 2: "RF-08 Insumos — Must — Dado insumo registrado, Cuando descuento por asignación, Entonces stock por lote actualizado".
- Nota pie 6pt italic #5A5A5A: "Cada RF Must lleva Given/When/Then validado INVEST (ej. V-01 auth: Independiente, Negociable, Valiosa, Estimable, Pequeña, Verificable) — Fuente: Vallejo (2026) Anexo 7 p.52 + Tablas 7-18 pp.58-63".

Borde #A85C1E, fondo #FFF8F0, títulos #A85C1E. Exportar como fig_rf_prioridad.png
```

**Caption que se mantiene:** `Figura 1. 18 RF por prioridad (89% Alta) y criterios Gherkin — elaboración propia.`

---

## Validación final (ya aplicada en DOCX/PDF)
- [x] 1 placeholder por documento: `Figura 1 - Espacio reservado para diagrama (ver prompt adjunto)` con recuadro #A85C1E sobre #FFF8F0.
- [x] Caption `Figura 1. ... — elaboración propia` conservada debajo del placeholder.
- [x] 0 menciones de "Versión ultra-compacta" / "Versión compacta (≤5 págs.)" (portada limpia: `Check-in 1` + subtítulo sin sufijo).
- [x] Páginas PDF final: 6 hojas en los cuatro documentos (límite 6 incluida portada).
- [x] Imágenes originales removidas del flujo (quedan como media huérfana pero no renderizan; insertar nuevo PNG reemplazará).

## Entrega Moodle
Subir DOCX + PDF (3-4 págs.) + ZIP con PNGs generados por Claude. Video Teams: mostrar placeholder y luego PNG insertado a pantalla completa, explicando con citas APA 7.
