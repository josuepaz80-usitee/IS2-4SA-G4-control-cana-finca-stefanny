# Diagramas UML de comportamiento — versión corregida (Taller S5)

Diagramas de comportamiento del proceso de producción de caña de azúcar (registro de
producción y gestión de actividades y asignaciones), **rediseñados según los criterios
que la docente explicó en clase** (Ing. Andrea Sinche Guzmán, MSc., 4–12 de noviembre de 2026).

## Contenido

| Archivo | Diagrama | Elaborado por |
|---|---|---|
| `S5_Comportamiento_UML_Grupo4.pdf` | Documento oficial (todos los diagramas + especificación + checklist) | Grupo 4 |
| `diagramas/CU1_produccion_cosecha.*` | Casos de uso — Producción y Cosecha | Ayovi Mina Cindy |
| `diagramas/CU2_actividades_asignaciones.*` | Casos de uso — Actividades y Asignaciones | Parrales Franco Jodie |
| `diagramas/ACT_registrar_produccion.*` | Actividades — Registrar producción | Pazmiño Raimundi Henry |
| `diagramas/SEQ_registrar_produccion.*` | Secuencia — Registrar producción | Vera Yagual Mayra |

Cada diagrama en `.drawio` (editable) y `.png` (imagen).

## Criterios de la docente aplicados

- **Casos de uso:** actores (rol) fuera del rectángulo; casos adentro; asociación sin flecha;
  nombre verbo + cosa en singular; «include» = siempre y «extend» = a veces (flecha punteada
  sin relleno, etiqueta al lado sin fondo). «Consultar actividad» lo realizan Administrador y
  Trabajador.
- **Actividades:** nodo inicial (círculo negro) y final (anillo); acciones redondeadas con verbo;
  decisión en rombo con guardas [Sí]/[No]; particiones Trabajador y Sistema; sin flechas cruzadas.
- **Secuencia:** 4 líneas de vida MVC (Trabajador, :Pantalla, :Controlador, :BaseDatos); mensaje
  (flecha rellena) vs retorno (punteada abierta); barras de activación; mensajes numerados;
  decisión en fragmento «alt».
