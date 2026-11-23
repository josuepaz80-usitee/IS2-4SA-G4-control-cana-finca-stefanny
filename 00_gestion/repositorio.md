# Repositorio del equipo — IS2 4SA Grupo 4

**Creado:** 2026-11-07
**Cuenta:** `josuepaz80-usitee` (Henry Josué Pazmiño Raimundy)
**URL:** https://github.com/josuepaz80-usitee/IS2-4SA-G4-control-cana-finca-stefanny
**Visibilidad:** privado

## Contenido inicial (8 commits)

```
IS2-4SA-G4-control-cana-finca-stefanny/
├── README.md                                              ← tesis, integrantes, acuerdos
├── 01_tesis/VALLEJO_LOZADO_DIXON_JOSUE.pdf                 ← 1,5 MB
├── 02_historias/.gitkeep
├── 03_bpmn/
│   ├── asis.drawio · asis.png
│   └── tobe.drawio · tobe.png
└── 04_documento/Taller_BPMN_IS2_4SA_Grupo4_Pazmino.pdf
```

Los siete archivos se verificaron contra el original por tamaño: todos coinciden.

## Actualización 2026-11-15 — Check-in 2

Se subieron los entregables y diagramas del Check-in 2 (commit `6377c47`, rama `main`) en `05_checkins/CHK2_2026-11-15/`:

- `entregables/`: **4 PDF + 4 DOCX** (Henry §6+§9, Vera §10, Cindy §7+§8, Jodie §11).
- `diagramas/`: **11 diagramas draw.io + PNG** (V1 arquitectura, C1 clases, C2 E-R Chen, J1–J5 wireframes, H1 casos de uso, H2 secuencia, H3 actividades) + variante `H3_..._sintitulo`.
- `README.md` de la carpeta con el reparto y el detalle.

Método: `git clone` + commit + push (rama `main`); verificado por API (36 archivos: 4 PDF + 4 DOCX + 12 drawio + 11 png + README).

## Pendiente

1. **Agregar colaboradores** (Settings → Collaborators, o por API con el usuario de cada uno):
   Vera Yagual Mayra, Ayovi Mina Cindy, Parrales Franco Jodie. Falta que envíen su usuario de GitHub.
2. **Evidencia para Moodle:** captura de la lista de colaboradores y captura del primer commit.
   Deben tomarlas desde la cuenta, porque el repositorio es privado y no se ve sin sesión.

## Cómo se subió

Vía API de GitHub con el token del credential helper de git (`~/.git-credentials`,
cuenta `josuepaz80-usitee`, scope `repo`). Sin `gh` CLI instalado. Script:
`/tmp/subir_repo_is2.py` — las rutas con espacios se codifican y el nombre de la tesis se
sanitizó a `VALLEJO_LOZADO_DIXON_JOSUE.pdf`.
