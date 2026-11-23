# PROMPTS PARA CLAUDE — Diagramas del Check-in 2 en **draw.io** (IS2 · Grupo 4)

> **Todo se entrega como archivo `.drawio` (XML de draw.io / diagrams.net).** Nada de PlantUML ni SVG.
> Cómo usar: copia el bloque **PROMPT** de cada diagrama en Claude. Claude devuelve un XML (empieza con `<mxfile…`). Guárdalo como `NOMBRE.drawio` (Bloc de notas) y ábrelo en https://app.diagrams.net (o arrástralo). Para exportar: *Archivo → Exportar como → PNG*.
> **Atajo sin archivo:** en diagrams.net → *Extras → Editar diagrama…* → pega solo `<mxGraphModel> … </mxGraphModel>` → *Aceptar*.
> Regla fija: cada diagrama lleva un texto al pie **"Elaborado por: [Nombre del integrante]"**.

---

## CONTEXTO DEL PROYECTO (pégalo al inicio de CADA prompt)

```
CONTEXTO DEL PROYECTO
Rediseño del "Sistema web para el control de los procesos de producción de caña de azúcar en la
Finca Stefanny" (tesis de Vallejo Lozado, 2026), para Ingeniería de Software 2 (UAE, 4SA).
Proceso: preparación → siembra → riego → fertilización → control de plagas → monitoreo → cosecha.
Módulos (10): 1 Login, 2 Dashboard, 3 Usuarios, 4 Empleado (empleados/asistencia/permisos),
5 Lotes, 6 Insumos, 7 Actividades y Asignaciones, 8 Producción y Cosecha, 9 Análisis y Reportes, 10 Administración.
Roles del rediseño (RBAC): Administrador (todo), Operario/Técnico (registra producción y asistencia),
Auditor/Consulta (solo lectura de reportes y log).
Entidades/tablas (12): usuarios, empleado, control_asistencia, permisos_faltas, lotes, insumos,
actividades, asignaciones, plagas_enfermedades, produccion, analisis, administracion.
Textos en español. Notación UML 2.5 para los diagramas UML.
```

## REGLAS DE SALIDA EN DRAW.IO (pégalas al final de CADA prompt)

```
FORMATO OBLIGATORIO — DRAW.IO:
Devuelve ÚNICAMENTE el XML de draw.io, empezando por <mxfile host="app.diagrams.net"> … </mxfile>,
con este esqueleto exacto (una sola <diagram>):
<mxfile host="app.diagrams.net"><diagram id="d1" name="TITULO"><mxGraphModel dx="900" dy="700" grid="1" gridSize="10" guides="1" tooltips="1" connect="1" arrows="1" fold="1" page="1" pageScale="1" pageWidth="1169" pageHeight="826" math="0" shadow="0"><root><mxCell id="0"/><mxCell id="1" parent="0"/>
  <!-- aquí van las celdas (vértices y aristas) -->
</root></mxGraphModel></diagram></mxfile>
Sin explicaciones ni texto fuera del XML. Usa estos estilos:
- Texto/título: style="text;html=1;fontSize=16;fontStyle=1;align=center;"
- Rectángulo: style="rounded=0;whiteSpace=wrap;html=1;fillColor=#FBE9DA;strokeColor=#A85C1E;"
- Caja redondeada (acción): style="rounded=1;whiteSpace=wrap;html=1;fillColor=#FBE9DA;strokeColor=#A85C1E;arcSize=20;"
- Elipse (caso de uso): style="ellipse;whiteSpace=wrap;html=1;fillColor=#FBE9DA;strokeColor=#A85C1E;"
- Actor UML: style="shape=umlActor;verticalLabelPosition=bottom;verticalAlign=top;html=1;outlineConnect=0;"
- Rombo (decisión): style="rhombus;whiteSpace=wrap;html=1;fillColor=#FFFFFF;strokeColor=#A85C1E;"
- Círculo inicio/fin: style="ellipse;fillColor=#000000;strokeColor=#000000;" (30x30)
- Línea de vida: style="shape=umlLifeline;perimeter=lifelinePerimeter;whiteSpace=wrap;html=1;"
- Arista: <mxCell id="eX" style="endArrow=block;html=1;rounded=0;" edge="1" parent="1" source="ID1" target="ID2"><mxGeometry relative="1" as="geometry"/></mxCell>
- Arista con etiqueta: pon el texto en value de la arista. «include» → style="endArrow=open;dashed=1;html=1;" value="«include»".
- Vértice: <mxCell id="ID" value="Texto" style="…" vertex="1" parent="1"><mxGeometry x=".." y=".." width=".." height=".." as="geometry"/></mxCell>
- Clase UML: caja con value HTML multilínea: value="NombreClase&#10;—————&#10;- atributo: tipo&#10;—————&#10;+ metodo(): void" y style="swimlane;startSize=26;html=1;align=left;verticalAlign=top;fillColor=#FBE9DA;strokeColor=#A85C1E;"
- Al final agrega una celda de texto: value="Elaborado por: NOMBRE" abajo.
Ordena las coordenadas (x,y) para que no se solapen. Devuelve el XML completo y válido.
```

---

## VERA — §10 Arquitectura 3 capas (MVC)
**PROMPT #V1**
```
[CONTEXTO DEL PROYECTO]

TAREA: Dibuja un DIAGRAMA DE ARQUITECTURA EN TRES CAPAS (mapeo MVC). Tres bandas horizontales apiladas:
1) PRESENTACIÓN (Vista): rectángulo grande que contiene: Login, Dashboard, Registrar Producción,
   Gestionar Asignaciones, Reportes (HTML/CSS/Bootstrap, navegador).
2) LÓGICA DE NEGOCIO (Controlador): rectángulo con: AutenticaciónRBAC, ProduccionService,
   AsignacionService, AsistenciaService, ReporteService.
3) DATOS (Modelo): rectángulo con: Repositorios/DAO + Base de Datos MySQL (12 tablas).
Conecta las capas con flechas verticales de doble sentido (Vista↔Controlador↔Modelo). Solo la capa de
negocio toca la de datos (la vista NO se conecta directo a la base). Rótula cada banda.
Pie: "Elaborado por: Vera Yagual Mayra Alejandra". Devuelve solo el XML draw.io válido.

[REGLAS DE SALIDA EN DRAW.IO]
```

---

## CINDY — §7 Diagrama de clases · §8.1 Modelo E-R (Chen)
**PROMPT #C1 — Clases**
```
[CONTEXTO DEL PROYECTO]

TAREA: Dibuja un DIAGRAMA DE CLASES UML con: Usuario, Empleado, ControlAsistencia, PermisoFalta, Lote,
Insumo, Actividad, Asignacion, PlagaEnfermedad, Produccion, Analisis, Administracion.
Usa el formato de clase (swimlane con atributos/métodos). Relaciones:
- Herencia: Administrador, Operario y Auditor heredan de Usuario (triángulo de generalización).
- Agregación: Asignacion agrega a Empleado, Lote, Actividad e Insumo.
- Asociaciones con multiplicidad: Empleado 1—0..* ControlAsistencia; Empleado 1—0..* PermisoFalta;
  Lote 1—0..* Asignacion; Lote 1—0..* Produccion; Lote 1—0..* PlagaEnfermedad; Usuario 1—0..* Analisis.
Pie: "Elaborado por: Ayovi Mina Cindy Nicole". Devuelve solo el XML draw.io válido.

[REGLAS DE SALIDA EN DRAW.IO]
```
**PROMPT #C2 — E-R Chen**
```
[CONTEXTO DEL PROYECTO]

TAREA: Dibuja un MODELO ENTIDAD-RELACIÓN notación Chen. Entidades = rectángulos, atributos = elipses
(clave primaria subrayada con <u>…</u> en el value html), relación = rombos, cardinalidades 1 y N en las líneas.
Entidades: usuario(id_usuario*, nombre, correo, clave_hash, rol), empleado(id_empleado*, nombres, cedula,
celular, direccion, estado_laboral), control_asistencia(id_asistencia*, fecha, hora_entrada, hora_salida,
horas_trabajadas, estado), permisos_faltas(id_permiso*, tipo, motivo, fecha_ini, fecha_fin, estado),
lote(id_lote*, nombre, tamano, tipo_suelo, estado_fenologico, fecha_siembra), insumo(id_insumo*, tipo,
descripcion, stock, unidad), actividad(id_actividad*, tipo, descripcion), asignacion(id_asignacion*, estado,
fecha), plaga_enfermedad(id_plaga*, tipo, producto_aplicado, fecha), produccion(id_produccion*, fecha,
peso_kg, rendimiento, observaciones), analisis(id_analisis*, tipo, periodo), administracion(id_admin*,
nombre_finca, ruc, telefono, hectareas).
Relaciones (rombo): tiene_asistencia(empleado 1—N control_asistencia), tiene_permiso(empleado 1—N
permisos_faltas), se_asigna(lote 1—N asignacion, actividad 1—N asignacion, insumo 1—N asignacion),
tiene_plaga(lote 1—N plaga_enfermedad), produce(lote 1—N produccion), genera(usuario 1—N analisis).
Marca las FK en las entidades del lado N.
Pie: "Elaborado por: Ayovi Mina Cindy Nicole". Devuelve solo el XML draw.io válido.

[REGLAS DE SALIDA EN DRAW.IO]
```

---

## JODIE — §11 Wireframes (5 pantallas)
**PROMPT #J1–#J5** (mismo encabezado; cambia la PANTALLA)
```
[CONTEXTO DEL PROYECTO]

TAREA: Dibuja un WIREFRAME de baja fidelidad (solo rectángulos, líneas, texto de relleno y etiquetas
reales en español; SIN colores, escala de grises) de una pantalla de escritorio ~1000×650 px. Usa
rectángulos para zonas, texto para etiquetas de campos y botones. Al pie: "Elaborado por: Parrales Franco Jodie Mabel".
LA PANTALLA ES: [reemplaza aquí — ver abajo].
Devuelve solo el XML draw.io válido.

[REGLAS DE SALIDA EN DRAW.IO]
```
- **#J1 Login** → "Inicio de sesión: logo arriba, campos «Usuario» y «Contraseña», botón «Ingresar», enlace «Recuperar contraseña»."
- **#J2 Dashboard** → "Panel de control: barra lateral con los 10 módulos, 3 tarjetas KPI (Producción kg, Lotes activos, Insumos bajos) y un gráfico de barras de producción por lote."
- **#J3 Registrar producción** → "Formulario: combo «Lote», campo «Peso (kg)», campo «Fecha», área «Observaciones», botones «Guardar» y «Cancelar»."
- **#J4 Asignar actividad** → "Formulario: combos «Actividad», «Empleado», «Lote» e «Insumo», campo «Fecha», etiqueta «Estado: Pendiente», botón «Asignar»."
- **#J5 Reportes** → "Análisis y reportes: filtros (Fecha, Lote, Empleado), tabla de resultados y botones «Exportar PDF» y «Exportar Excel»."

---

## HENRY — §6 Casos de uso · §9 Secuencia y Actividades (opcional, para uniformar estilo)
**PROMPT #H1 — Casos de uso**
```
[CONTEXTO DEL PROYECTO]

TAREA: Dibuja un DIAGRAMA DE CASOS DE USO UML. Actores (izquierda): Administrador, Operario/Técnico,
Auditor/Consulta (forma de actor UML). Frontera del sistema: rectángulo grande titulado "Sistema web de
control de producción — Finca Stefanny (rediseño)". Casos de uso (elipses): Iniciar sesión, Gestionar
usuarios y roles (RBAC), Registrar producción (cosecha), Asignar actividad a empleado·lote·insumo,
Registrar asistencia, Justificar falta/permiso, Consultar reportes, Auditar registro de acciones (log).
Asociaciones: Administrador→(login, gestión usuarios, asignar, registrar producción, reportes);
Operario→(login, registrar producción, registrar asistencia); Auditor→(login, reportes, auditar).
Include («include», línea discontinua): Registrar producción/asistencia/consultar reportes ..> Iniciar sesión.
Extend («extend»): Justificar falta ..> Registrar asistencia.
Pie: "Elaborado por: Pazmiño Raimundy Henry Josué". Devuelve solo el XML draw.io válido.

[REGLAS DE SALIDA EN DRAW.IO]
```
**PROMPT #H2 — Secuencia (CU01)**
```
[CONTEXTO DEL PROYECTO]

TAREA: Dibuja un DIAGRAMA DE SECUENCIA UML (4 líneas de vida con shape=umlLifeline): Operario, :Pantalla,
:ControladorProduccion, :BaseDatos. Mensajes (flechas horizontales numeradas):
1 Operario→Pantalla: seleccionar «Registrar producción»; 2 Operario→Pantalla: ingresar lote, peso y fecha;
3 Pantalla→Controlador: enviarFormulario(datos); 3.1 Controlador→Controlador: validar() (auto-llamada);
[alt datos válidos]: 4 Controlador→BaseDatos: guardarProduccion(datos); 5 BaseDatos→Controlador: idRegistro;
6 Controlador→Pantalla: resultado OK; 7 Pantalla→Operario: «Producción registrada».
[else datos inválidos]: Controlador→Pantalla: error; Pantalla→Operario: «Datos no válidos».
Dibuja un marco "alt" (rectángulo) que encierre los mensajes 4-7 con etiqueta "else".
Pie: "Elaborado por: Pazmiño Raimundy Henry Josué". Devuelve solo el XML draw.io válido.

[REGLAS DE SALIDA EN DRAW.IO]
```
**PROMPT #H3 — Actividades (CU01)**
```
[CONTEXTO DEL PROYECTO]

TAREA: Dibuja un DIAGRAMA DE ACTIVIDADES UML con DOS PARTICIONES (rectángulos verticales titulados)
"Trabajador" y "Sistema". Flujo: inicio (círculo negro) → [Trabajador] Elegir «Registrar producción» →
[Sistema] Mostrar formulario → [Trabajador] Ingresar lote, peso y fecha → [Sistema] Validar datos →
rombo "¿Datos válidos?": [Sí] → [Sistema] Guardar registro → [Sistema] Mostrar «Producción registrada» → fin;
[No] → [Sistema] Mostrar error → vuelve a "Ingresar lote, peso y fecha" (flecha etiquetada "corregir").
Pie: "Elaborado por: Pazmiño Raimundy Henry Josué". Devuelve solo el XML draw.io válido.

[REGLAS DE SALIDA EN DRAW.IO]
```

---

### Cómo abrir lo que devuelve Claude (draw.io)
1. **Archivo:** copia el XML completo → guárdalo como `NOMBRE.drawio` → ábrelo en app.diagrams.net (arrastrar) .
2. **Rápido:** app.diagrams.net → *Extras → Editar diagrama…* → pega solo `<mxGraphModel …> … </mxGraphModel>` → *Aceptar*.
3. Exporta: *Archivo → Exportar como → PNG* → pégalo en el recuadro del documento del integrante.
