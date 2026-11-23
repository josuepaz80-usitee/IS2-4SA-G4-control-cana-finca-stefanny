# Informe de Factibilidad — Selección de Tesis para Proyecto Ingeniería de Software II
**Estudiante:** Henry Josué Pazmiño Raimundy — 4to semestre (2026-2027 CII) — Paralelo 4SA  
**Docente:** Ing. Andrea Sinche Guzmán, MSc.  
**Fecha:** 18-oct-2026  
**Repositorio:** https://cia.uagraria.edu.ec — TESIS.INF (Computación Guayaquil)  
**Guía:** Guia_Proyecto_ING_SW2_2026.pdf (9 págs) — peso 2.5 por parcial

---

## Objetivo
Evaluar 7 tesis candidatas (11 PDFs descargados) que cumplen: Carrera Computación Guayaquil + sistema agro/producción + disponible en CIA, y recomendar la ideal por **sencillez y practicidad** para cumplir: 4+ módulos + autenticación con roles, BPMN as-is/to-be, UML, ER, wireframes, seguridad, LOPDP y casos de prueba sin deuda técnica.

---

## Metodología
- Descarga directa CIA con `curl -L` verificación HTTP 200 y `file` PDF 1.7
- Extracción `pymupdf 1.28.2` primeras 15 páginas + índice + diccionario + anexos
- Lectura completa Vallejo (112p) con análisis subagente; muestreo rápido resto
- Criterios: claridad del proceso, nº entidades, complejidad técnica (web vs IoT/predictivo), vacíos de seguridad/LOPDP (oportunidad de rediseño), esfuerzo estimado días, riesgo Turnitin/IA

Archivos en `tesis-candidatas/` (17 MB totales, 11 PDFs verificados):
- VALLEJO LOZADO DIXON JOSUE.pdf (112p, 1.5M)
- SICHA SUMBA ROSA ALEXANDRA.pdf (104p, 1.3M)
- MENDEZ/VILLEGAS MONTE VERDE (132p, 1.5M x2 idénticos)
- RUIZ/VALDIVIESO PITAHAYA (159p, 1.6M x2 idénticos) — ojo 159p no 20p como se anunció inicialmente
- GONZALEZ ALVARADO GENESIS CECILIA.pdf (101p, 1.4M)
- MIRANDA/PORTOCARRERO HIDROPONÍA (113p, 1.6M x2 idénticos)
- ANDRADE/CORNEJO BANANO ROSA MATILDE (137p, 1.5M x2 idénticos)

---

## Tabla comparativa rápida

| # | Tesis (título corto) | Pág | Autor(es) | Dominio | Módulos reales | Stack | Seguridad/LOPDP existente | Complejidad rediseño |
|---|---|---|---|---|---|---|---:|---|
| **1** | **CAÑA STEFANNY - Vallejo** | 112 | Vallejo Dixon | Caña azúcar 6ha, La Troncal | **10 + 6 submódulos** (login, dashboard, usuarios, empleados/asistencia/permisos, lotes, insumos, actividades/asignaciones/plagas, producción/cosecha, reportes 7 tipos, administración/backup) | PHP/MySQL/Bootstrap/XAMPP/Hostinger + XP | Cita LOPDP art.37 pero sin aviso/consent/ARCO; contraseña nvarchar sin hash, sin CSRF/XSS, backup sin cifrado | **SIMPLE** |
| 2 | CACAO MONILIASIS CHABLA - Sicha | 104 | Sicha Rosa Alexandra | Cacao predictivo finca Chabla | Usuarios, lotes, monitoreo, predicción monilia, reportes | PHP/MySQL + modelo predictivo | Menciona seguridad, sin STRIDE, sin LOPDP operativo | **MEDIA** (predictivo añade ML) |
| 3 | MONTE VERDE - Mendez/Villegas | 132 | Mendez Byron + Villegas Josue | Cacao producción+comercialización+insumos | Producción, insumos, comercialización, ventas, inventario, reportes | PHP/MySQL/Bootstrap + XP | Sin RBAC, sin LOPDP | **MEDIA-ALTA** (triple alcance) |
| 4 | PITAHAYA LA QUERENCIA - Ruiz/Valdivieso | 159 | Ruiz William + Valdivieso Jonathan | Pitahaya trazabilidad Hacienda La Querencia | Trazabilidad lote→cosecha→empaque→exportación, lotes, producción, calidad | PHP/MySQL/Bootstrap | Cita exportación, sin seguridad profunda | **MEDIA-ALTA** (159p, más extensa) |
| 5 | MAÍZ Zea mays - Gonzalez | 101 | Gonzalez Genesis Cecilia | Maíz El Triunfo | Lotes, siembra, riego, fertilización, seguimiento fenológico, cosecha | PHP/MySQL | Básica | **SIMPLE** |
| 6 | HIDROPONÍA LECHUGA LA HILDA - Miranda/Portocarrero | 113 | Miranda Marcos + Portocarrero Ulvio | Lechuga hidropónica + monitoreo ambiental IoT | Sensores, variables ambientales, riego, nutrientes, dashboard IoT | Arduino/IoT + PHP/MySQL | Sin hardening IoT | **COMPLEJA** (hardware) |
| 7 | BANANO ROSA MATILDE - Andrade/Cornejo | 137 | Andrade Michael + Cornejo Steven | Banano predicción producción | Lotes, producción, predicción, reportes, costos | PHP/MySQL + predictivo | Sin seguridad avanzada | **MEDIA** |

> Todas cumplen repositorio CIA TESIS.INF y temática agro — ninguna es externa.

---

## Análisis por tesis (sencillez → complejidad)

### 1) VALLEJO - Caña Stefanny — RECOMENDADA #1 (GANADORA POR SENCILLEZ)
**Por qué es la más simple y práctica:**
- Proceso lineal 7 etapas (preparación → siembra → riego → fertilización → plagas → monitoreo → cosecha) perfectamente modelable en **2-3 BPMN** (AS-IS manual vs TO-BE digital). Narrado en p.25-27 + ficha observación p.51
- **12 tablas** con diccionario completo (usuarios, empleado, control_asistencia, permisos_faltas, lotes, insumos, actividades, asignaciones, plagas_enfermedades, producción, análisis, administración) — ER ya existe Apéndice 2 p.101, solo refinar FKs/índices
- 9 casos de uso en Lucidchart (Anexos 9-17) + UI Bootstrap + pruebas por módulo (Tablas 19-27) + manual técnico/usuario — **reutilizas 70%**
- **Vacíos perfectos para IS2:** BPMN inexistente (0 menciones), RBAC con solo rol 'Administrador' (empleado no es usuario), sin hash/bcrypt, sin CSRF/XSS, sin logs, sin LOPDP operativo (solo art.37 genérico), backup sin cifrado, recuperación por correo sin token
- 1 solo usuario real (propietario) — sin concurrencia, foco en diseño
- **Esfuerzo estimado 7-10 días totales:** BPMN+UML retoque 1-2d, ER 0.5d, RBAC 2-3d, hardening 1-2d, LOPDP 1d, pruebas 2d
- Inconsistencia menor Freire/Quinteros fácil de corregir, demuestra análisis crítico

**Ideal para grupo de hasta 5:** cada integrante toma 2 módulos (ej. 1: BPMN+auth, 2: lotes/insumos, 3: actividades/asignaciones, 4: producción/reportes, 5: seguridad/LOPDP/pruebas) — cumple video individual sin pisarse.

### 2) GONZALEZ - Maíz — RECOMENDADA #2 (PLAN B SIMPLE)
- Dominio maíz (cultivo nacional, proceso estándar) — similar linealidad a caña, 101p manejables, metodología cualitativa + XP
- Menos páginas que Vallejo, buena alternativa si Vallejo ya está tomada en tu paralelo 4SA
- Vacíos similares (sin RBAC, sin seguridad) — también fácil de ampliar

### 3) SICHA - Cacao moniliasis predictivo — MEDIA
- Valor académico alto (Moniliophthora roreli + predictivo) pero **añade complejidad ML** que deberás rediseñar (¿qué modelo? ¿qué dataset? ¿cómo validar predicción?). Bien si tu grupo quiere lucirse con IA, mal si buscas sencillez
- 104p, pero requiere casos de prueba de modelo predictivo (particiones no triviales)

### 4) MONTE VERDE - Triple alcance — MEDIA-ALTA
- Ventaja: ya cumple 4+ módulos de sobra (producción + insumos + comercialización + ventas). Desventaja: **132p y 3 flujos** = más diagramas, más ER, más historias (mínimo 10 pero aquí necesitarás 15+ para cubrir todo). Se vuelve pesada para 7-10 días
- Tesis en pareja (2 PDFs idénticos, 1 tesis) — debes registrarla como una sola elección

### 5) PITAHAYA La Querencia — MEDIA-ALTA (más extensa)
- 159p, la más larga — trazabilidad es excelente para LOPDP y BPMN, pero **más contenido = más para parafrasear APA7 y más para criticar**. Riesgo de exceder alcance en Entrega1 29 nov
- También en pareja

### 6) BANANO Rosa Matilde — MEDIA
- 137p, predicción + control — similar a Sicha, intermedia. Buen dominio banano (exportación) pero predictivo añade capa estadística

### 7) HIDROPONÍA La Hilda — COMPLEJA (NO RECOMENDADA PARA SENCILLEZ)
- **IoT + hardware (sensores, variables ambientales, prototipo hidropónico)** — si tu rediseño debe ser solo modelado (sin programar, según Guía p.1), tendrás que modelar hardware, lo que complica BPMN, secuencia y arquitectura 3 capas
- 113p + 2 autores, metodología prototipado — hermosa pero la más arriesgada para cumplir rápido

---

## Ranking final por SENCILLEZ Y PRACTICIDAD

1. **VALLEJO - Caña Stefanny** — 9.2/10 — simple, completa, vacíos ideales, 112p, 10 módulos claros
2. **GONZALEZ - Maíz** — 8.8/10 — simple, 101p, proceso lineal, plan B perfecto
3. **SICHA - Cacao predictivo** — 7.5/10 — buena pero predictivo sube complejidad
4. **BANANO Rosa Matilde** — 7.2/10 — similar
5. **MONTE VERDE** — 6.8/10 — completa pero triple alcance alarga trabajo
6. **PITAHAYA** — 6.5/10 — trazabilidad valiosa pero 159p pesa
7. **HIDROPONÍA** — 5.0/10 — IoT la hace compleja para IS2 puro software

---

## Recomendación para tu grupo

**Elige VALLEJO (caña Stefanny).** Si al ir a Moodle ya está tomada en 4SA, ve directo a GONZALEZ (maíz) como plan B — avísame y te preparo la ficha en 1h.

**Próximos pasos (según Guía p.5):**
1. Verifica en Moodle → Elección tesis → si Vallejo/Gonzalez sigue libre en 4SA (recuerda: 1 tesis = 1 equipo por paralelo)
2. Yo te armo: ficha tesis parafraseada APA7 + tabla crítica original vs rediseño + BPMN AS-IS/TO-BE preliminares + 10 historias + propuesta RBAC 3 roles (Admin / Técnico campo / Auditor) lista para CHK1 (1 nov)
3. Entrega1 29 nov: incorporamos UML clase/secuencia/actividades + ER refinado + wireframes 5 pantallas + matriz trazabilidad

¿Confirmas Vallejo o prefieres que prepare las dos fichas (Vallejo + Gonzalez) para que elijas con tu grupo?
