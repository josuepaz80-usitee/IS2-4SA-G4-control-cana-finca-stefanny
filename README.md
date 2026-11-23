# IS2-4SA-G4 — Control de producción de caña de azúcar · Finca Stefanny

Repositorio de trabajo del **Grupo 4** para el proyecto de **Ingeniería en Software II**
(Universidad Agraria del Ecuador · Computación en Línea · 4SA · 2026–2027 CII).

**Docente:** Ing. Andrea Sinche Guzmán, MSc.

## Tesis de origen

| Campo | Dato |
|---|---|
| **Título** | Sistema web para el control de los procesos de producción de caña de azúcar en la Finca Stefanny |
| **Autor** | Vallejo Lozado Dixon Josué |
| **Tutor** | Ing. Jara Obregón Luis Stalin, MSc |
| **Institución** | Universidad Agraria del Ecuador — Facultad de Ciencias Agrarias — Carrera de Computación |
| **Año** | 2026 |
| **Metodología** | XP (Extreme Programming) |
| **Stack de la tesis** | PHP + MySQL + HTML/CSS/JavaScript + Bootstrap |

> El proyecto **no resume la tesis**: la critica y propone el rediseño del sistema, siguiendo la
> guía de la asignatura.

## Integrantes

| # | Nombre | Aporte principal hasta el Check-in 1 |
|---|---|---|
| 1 | Vera Yagual Mayra Alejandra | §1 Ficha · §2.1 Organización · §2.2 Actores |
| 2 | **Pazmiño Raimundy Henry Josué** | §5 Crítica del diseño · ranking C1–C7 |
| 3 | Ayovi Mina Cindy Nicole | §3 Modelo del proceso (BPMN as-is) |
| 4 | Parrales Franco Jodie Mabel | §4 Historias · §4.1 Tablero Kanban · §5 MoSCoW |

## Estructura del repositorio

```
IS2-4SA-G4-control-cana-finca-stefanny/
├── README.md                  ← este archivo
├── 01_tesis/                  ← tesis de origen (PDF)
├── 02_historias/              ← historias de usuario y tablero
├── 03_bpmn/                   ← diagramas de proceso
│   ├── asis.drawio · asis.png
│   └── tobe.drawio · tobe.png
├── 04_documento/              ← documento de entrega
└── 06_uml_comportamiento/     ← diagramas UML de comportamiento (S5, corregidos) + documento
```

Los diagramas se guardan en **`.drawio`** (editable y comparable en Git) y en **`.png`**
(imagen para el documento y para Moodle).

## Acuerdos del equipo

- **Una sola versión vigente:** todo cambio entra por commit, no por archivos «final_final_v3».
- **Mensajes de commit claros:** `Agrega BPMN as-is del registro de cosecha`, no `cambios`.
- **Rama principal:** `main`. Para aportes grandes, rama propia y luego *merge*.
- **Nada de credenciales** dentro del repositorio.

## Referencias del marco

- Object Management Group. (2011). *Business Process Model and Notation (BPMN), version 2.0*.
  https://www.omg.org/spec/BPMN/2.0
- Sommerville, I. (2016). *Software engineering* (10th ed.). Pearson.
- Chacon, S., & Straub, B. (2014). *Pro Git* (2nd ed.). Apress. https://git-scm.com/book/es/v2
