# PLAN DE PROYECTO — Ingeniería de Software II — Caña Stefanny

**Materia:** Ingeniería de Software II — Ing. Andrea Sinche Guzmán, MSc. (Graciela Sinche G. — horario oficial)
**Proyecto:** *Rediseño de sistemas de software para el agro* — Expediente de diseño listo para implementar
**Tesis base elegida:** **SISTEMA WEB PARA EL CONTROL DE LOS PROCESOS DE PRODUCCIÓN DE CAÑA DE AZÚCAR EN LA FINCA STEFANNY** — Vallejo Lozado Dixon Josue (2026) — `TESIS.INF.CIA2.JUL.2026` — 112 págs — Finca Stefanny 6ha, La Troncal
**Grupo:** 4 integrantes — Vera Yagual Mayra, Pazmiño Henry, Ayovi Cindy, Parrales Jodie — Paralelo 4SA — 2026-2027 CII
**Repositorio tesis:** https://cia.uagraria.edu.ec — TESIS.INF (Computación Guayaquil)
**Carpeta proyecto:** `~/.hermes/memory/personal/estudios/semestre-4/04-ingenieria-software-2/proyecto/`
**Guía docente:** `material/Guia_Proyecto_ING_SW2_2026.pdf` + `material/Guia_Proyecto_ING_SW2_2026.md`

> **Regla de oro (Guía p.4):** Check-in = nota **individual** 0.50 | Entrega = nota **grupal** | Video = nota **individual** — si no apareces explicando tu parte = CERO.

---

## Ubicación de archivos

```
proyecto/
├── tesis-base/
│   ├── VALLEJO LOZADO DIXON JOSUE.pdf   (tesis completa CIA - 112p)
│   └── ANALISIS-VALLEJO.md              (extracción pymupdf + análisis vacíos)
├── INFORME_FACTIBILIDAD_TESIS_IS2.md    (7 tesis evaluadas - ranking)
├── PLAN-PROYECTO-IS2-CANA-STEFANNY.md   (este plan)
├── check-ins/
│   ├── CHK1_2026-11-01/
│   ├── CHK2_2026-11-15/
│   ├── CHK3_2027-01-10/
│   └── CHK4_2027-01-24/
├── entrega-1-29nov/                     (E1 - 50% - Unid.1-2)
│   └── E1_4SA_Grupo4_CanaStefanny/
└── entrega-2-14feb/                     (E2 - 100% - Unid.3-4)
tesis-candidatas/                        (6 tesis descartadas + informe original)
```

Tesis original también en `tesis-candidatas/` para comparativa.

---

## Cronograma oficial (Guía p.5) — Domingos 23:59 por Moodle

| Hito | Fecha | Peso | Responsable | Estado |
|---|---|---|---|---|
| **Elección tesis + registro equipo Moodle** | Semanas 1-2 (hasta ~26 oct 2026) | — | Grupo 4 | ✅ Hecho 18 oct - Vallejo elegida |
| **Check-in 1** | Dom 1 nov 2026 23:59 | 0.50 ind | Cada integrante | ⏳ Pendiente |
| **Check-in 2** | Dom 15 nov 2026 23:59 | 0.50 ind | Cada integrante | ⏳ |
| **ENTREGA 1 — 50%** | Dom 29 nov 2026 23:59 | 1.50 grupal | Grupo 4 | ⏳ |
| **Check-in 3** | Dom 10 ene 2027 23:59 | 0.50 ind | Cada integrante | ⏳ |
| **Check-in 4** | Dom 24 ene 2027 23:59 | 0.50 ind | Cada integrante | ⏳ |
| **ENTREGA 2 — 100% (final)** | Dom 14 feb 2027 23:59 | 1.50 grupal | Grupo 4 | ⏳ |

Total proyecto por parcial: **2.5** (0.5+0.5+1.5) — Turnitin 0-20% ok, 21-40% revisa docente (-0.30 si citas mal), 41%+ = CERO. IA >40% = CERO.

---

## Checklist Entrega 1 — 13 puntos (Guía p.6) — Fecha: 29 nov

- [x] **Tesis elegida y anunciada** — Vallejo Caña Stefanny — informe factibilidad 18 oct
- [ ] **1. Primera página obligatoria** — proyecto, tesis origen, integrantes (dos nombres/dos apellidos), paralelo/equipo, nº entrega, fecha, link video Teams (acceso "Cualquier persona con el enlace")
- [ ] **2. Fundamento teórico por sección** — palabras propias + ≥1 cita APA7 por sección
- [ ] **3. Ficha tesis** — título, autor, año, organización, problema (parafraseado APA7, no copiar texto/diagramas)
- [ ] **4. Descripción proceso actual y actores** — narrativa 7 etapas + actores (Admin único vs Empleado sin login)
- [ ] **5. BPMN as-is y to-be** — con carriles por actor + explicación mejora (Bizagi/draw.io) — **crear desde cero** (Vallejo tiene 0 BPMN)
- [ ] **6. Historias de usuario ≥10 con criterios aceptación + captura Kanban**
- [ ] **7. Tabla crítica original vs rediseño** — qué está incompleto/incorrecto/ausente
- [ ] **8. Diagrama casos de uso + especificación textual** — 9 existentes en Lucidchart, refinar + añadir RBAC
- [ ] **9. Diagrama clases, ER y diccionario** — ER Apéndice 2 p.101 + 12 tablas p.58-63, normalizar, añadir hash, FKs, índices
- [ ] **10. Diagramas secuencia y actividades** — flujo asignación actividad-empleado-lote-insumo y producción
- [ ] **11. Arquitectura 3 capas (MVC conceptual) + principios diseño**
- [ ] **12. Wireframes ≥5 pantallas** — Figma
- [ ] **13. Distribución trabajo visible en video** — video 12 min Teams, todos con cámara y diagrama abierto, coincide con check-ins (3 NO: no leer guion, no imágenes estáticas, no hablar por otro)

**Video E1:** 12 min max Teams — grabar reunión → ··· → Iniciar grabación → cada uno comparte pantalla con diagrama abierto → detener → Compartir → Copiar enlace → verificar "Cualquier persona con el enlace puede ver"

---

## Checklist Entrega 2 — 11 puntos (Guía p.7) — Fecha: 14 feb

- [ ] **1. Entrega 1 corregida**
- [ ] **2. Fundamento teórico por sección** (cita APA7)
- [ ] **3. Análisis seguridad diseño original** — Vallejo: sin hash, sin CSRF/XSS, etc.
- [ ] **4. Requisitos seguridad + principios diseño seguro** — auth, autorización, roles
- [ ] **5. Casos de mal uso ≥5 + STRIDE**
- [ ] **6. Matriz cumplimiento LOPDP** — datos, finalidad, medidas (cédula/celular en reportes Gmail sin cifrado)
- [ ] **7. Estándares y convenciones codificación**
- [ ] **8. Casos de prueba caja negra** — particiones equivalencia + valores límite
- [ ] **9. Backlog priorizado + matriz trazabilidad** — requisito–diseño–prueba
- [ ] **10. Documentación técnica + manual usuario preliminar**
- [ ] **11. Conclusiones (1 por integrante) + bibliografía APA7 + anexos**

**Video E2:** 12 min — cada uno explica seguridad o pruebas con diagrama/tabla abierta

---

## Checklist Check-ins (Guía p.7 pie) — Formato: aporte + sección plantilla + imagen avance

- [ ] **CHK1 (1 nov):** Elección tesis, análisis sistema existente — ficha + proceso actual + BPMN as-is borrador
- [ ] **CHK2 (15 nov):** Avance rediseño — casos uso / clases / modelo / wireframes
- [ ] **CHK3 (10 ene):** Avance diseño seguro — amenazas, LOPDP
- [ ] **CHK4 (24 ene):** Avance pruebas y trazabilidad

> Cada check-in debe ser aporte único por integrante (no repetir con otro compañero) + captura evidencia concreta del avance (no "nos reunimos", sino diagrama/código/tabla real). Sin captura = 50% nota.

---

## Avance realizado — 18 oct 2026

| Fecha | Avance | Ubicación | Responsable |
|---|---|---|---|
| 18 oct | Descarga 11 PDFs CIA (17MB) verificación HTTP 200 + file PDF 1.7 | `tesis-candidatas/` | Fredo/Henry |
| 18 oct | Extracción pymupdf + análisis Vallejo 112p (10 módulos, 12 tablas, 9 CU, vacíos seguridad/LOPDP) | `proyecto/tesis-base/ANALISIS-VALLEJO.md` | Fredo |
| 18 oct | Informe factibilidad 7 tesis — ranking sencillez (Vallejo #1 9.2/10) | `proyecto/INFORME_FACTIBILIDAD_TESIS_IS2.md` + `tesis-candidatas/` | Fredo |
| 18 oct | Anuncio WhatsApp Grupo 4 — Vallejo elegida | Mensaje listo para enviar | Fredo |
| 18 oct | Ubicación tesis elegida en carpeta proyecto + creación plan | `proyecto/tesis-base/VALLEJO...pdf` + este PLAN | Fredo |

**Pendiente inmediato (esta semana):**
- [ ] Registrar tesis Vallejo en Moodle (actividad Elección) — primero que registra gana (1 tesis = 1 equipo por paralelo)
- [ ] Enviar anuncio WhatsApp oficial al grupo curso 4SA
- [ ] Iniciar Ficha tesis + BPMN as-is (insumo para CHK1)

---

## Formato entrega (Guía p.8)

| Elemento | Nombre / formato | Dónde |
|---|---|---|
| Documento Word | `E1_4SA_Grupo4_CanaStefanny.pdf` | Turnitin directo |
| Archivos fuente | `E1_4SA_Grupo4_Anexos.zip` (.bpm, .drawio, .mdj, .puml, PDF wireframes) | Tarea Anexos |
| Video | Grabación Teams | Link en primera página |
| Check-in | `CHKn_4SA_Grupo4_Apellido.docx` | Tarea individual |

**Turnitin:** 0-20% ok, 21-40% revisa docente (si citas bien se acepta, si no -0.30), 41%+ = CERO y reporte. IA >40% = CERO.

---

## Próximos pasos sugeridos

1. **Esta semana:** Registrar tesis + enviar anuncio + validar con docente que Vallejo sigue libre en 4SA
2. **Semana 20-26 oct:** Ficha + proceso actual + actores + BPMN as-is borrador (base CHK1)
3. **Semana 27 oct-1 nov:** BPMN to-be + 10 HU + Kanban + tabla crítica → subir CHK1 individual
4. **2-15 nov:** UML retocado + ER refinado + wireframes → CHK2

¿Avanzamos con la Ficha tesis parafraseada APA7 + BPMN as-is?
