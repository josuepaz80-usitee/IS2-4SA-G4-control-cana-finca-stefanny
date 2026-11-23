# Análisis Tesis — VALLEJO LOZADO DIXON JOSUE

**Fuente:** `~/.hermes/memory/personal/estudios/semestre-4/04-ingenieria-software-2/tesis-candidatas/VALLEJO LOZADO DIXON JOSUE.pdf`
**Extracción:** Python `pymupdf 1.28.2` — 112 páginas totales, primeras 15 + índice + anexos clave
**Fecha análisis:** 2026-10-18

---

## 1. Ficha bibliográfica

| Campo | Valor |
|---|---|
| **Título exacto** | **SISTEMA WEB PARA EL CONTROL DE LOS PROCESOS DE PRODUCCIÓN DE CAÑA DE AZÚCAR EN LA FINCA STEFANNY** |
| **Autor** | VALLEJO LOZADO DIXON JOSUE — C.I. 0302556105 |
| **Tutor** | Ing. Jara Obregón Luis Stalin, MSc |
| **Institución** | Universidad Agraria del Ecuador — Facultad de Ciencias Agrarias — Carrera de Computación — Programa Regional de Enseñanza El Triunfo |
| **Año** | 2026 (defensa 21-04-2026; creación PDF 11-05-2026) |
| **Páginas** | 112 |
| **Metodología dev** | XP (Extreme Programming) — 5 fases: planificación, diseño, codificación, pruebas, implementación |
| **Stack** | PHP + MySQL + HTML/CSS/JavaScript + Bootstrap + XAMPP + VS Code + Hostinger |
| **Aprobación** | Tribunal: Torres Jaramillo Luis (presidente), Pilaloa David Wilmer, Alvarado Aguayo Allan |

---

## 2. Organización y problema

**Organización:** Finca **Stefanny** — 6 hectáreas de caña de azúcar — Parroquia Manuel de J. Calle, sector La Virgilia, cantón La Troncal (lat -2.357074, lon -79.413723). Propietario citado como **Antonio Freire** (resumen p.vii) / **Antonio Quinteros** (entrevista p.25) — inconsistencia menor a resolver.

**Problema central (p.2-3, 25-27):**
- Registro manual en libretas, sin respaldo digital ni centralización.
- Pérdida de datos, duplicidad, registros incompletos.
- Sin planificación formal — planificación verbal, tareas mal asignadas, demoras y doble trabajo.
- Sin control de insumos por lote/actividad (fertilizantes, herbicidas, pesticidas).
- Sin trazabilidad en tiempo real (arado, siembra, riego, fertilización, control plagas/malezas, monitoreo crecimiento, cosecha).
- Sin indicadores de rendimiento ni reportes — retrasa toma de decisiones.
- Población del estudio: **1 persona** (propietario/administrador) — enfoque cualitativo, descriptivo + documental, no experimental, sin muestreo estadístico.

**Objetivo general (p.6):** Desarrollar un sistema web responsive para el control y seguimiento eficiente de los procesos de producción de caña de azúcar en la finca Stefanny.

---

## 3. Módulos del sistema (p.4-6, 27-28, 52-53 — Tabla RF-01 a RF-18)

> El índice promete 8 módulos; el detalle real son **10 módulos principales + 6 submódulos** — supera holgadamente el mínimo de 4.

| # | Módulo | Descripción clave |
|---|---|---|
| 1 | **Inicio de sesión** | Login usuario/contraseña → panel de control; incluye "Restablecer clave" por correo (CU5) |
| 2 | **Panel de control (Dashboard)** | Accesos directos + gráficos: asistencia, producción por lote, consumo insumos, actividades |
| 3 | **Gestión de usuarios** | CRUD único usuario administrador (crear/editar/cambiar clave/eliminar/estado) |
| 4 | **Control del Empleado** | **Submódulos:** (4a) Gestión empleados — nombres, cédula, celular, dirección, estado laboral Con/Sin labor; (4b) Control asistencia — fecha, hora entrada/salida, horas trabajadas, estado Presente/Tardanza/Falta; (4c) Permisos y faltas — tipo, motivo, fechas, estado Pendiente/Aprobado |
| 5 | **Registro de Lotes** | CRUD lotes: nombre, tamaño, tipo suelo, estado fenológico, estado actual, fecha siembra |
| 6 | **Control de Insumos y Recursos** | Inventario: fertilizantes, herbicidas, pesticidas, semillas, herramientas — tipo, descripción, stock, unidad |
| 7 | **Actividades y Asignaciones** | (7a) Gestión actividades — siembra, fertilización, riego, mantenimiento, cosecha; (7b) Gestión asignaciones — asigna actividad → empleado + lote + insumos, estado pendiente/culminada; (7c) Plagas y enfermedades — registro casos + producto químico aplicado |
| 8 | **Producción y Cosecha** | Registro resultados por lote/fecha/campaña, rendimiento, observaciones; export PDF/Excel + envío Gmail |
| 9 | **Análisis y Reportes** | 7 reportes tipificados + gráficos comparativos + filtros avanzados (fecha, lote, empleado, insumo, plaga, estado, periodo) + export PDF/Excel/imprimir/envío Gmail: empleados, asistencia, permisos/faltas, lotes, actividades, plagas, producción |
| 10 | **Administración** | Datos finca (nombre, RUC, teléfono, dirección, hectáreas totales, frase bienvenida) + **copia y restauración de BD** (dump upload) |

**RF:** 18 requerimientos funcionales priorizados (16 Alta, 2 Media) — ver Anexo 7 p.52.

---

## 4. Actores / Roles

| Actor | Rol en el sistema | Evidencia |
|---|---|---|
| **Administrador** (propietario) | Único usuario autenticado — acceso total a los 10 módulos | Todos los casos de uso (Anexos 9-17) dicen "El administrador ..." — tabla `usuarios.rol` default `'Administrador'` |
| **Empleado agrícola** | **NO es usuario del sistema** — es entidad gestionada (tabla `empleado`) | Sin credenciales, sin login |
| **(Ausente)** | Sin roles diferenciados | Búsqueda `roles`: 0 resultados; `rol`: 117 menciones pero solo valor 'Administrador' |

**Brecha para IS2:** El requisito "auth + roles" no se cumple con un solo rol. Se debe introducir al menos **2-3 roles** (ej. Administrador, Operario/Técnico de campo, Consulta/Auditor) con matriz de permisos por módulo, y separar "empleado" de "usuario del sistema" si se desea login para operarios.

---

## 5. Diagramas y modelado

| Artefacto | ¿Existe? | Detalle | Ubicación tesis |
|---|---|---|---|
| **BPMN** | **NO** — 0 menciones en 112 páginas | No hay AS-IS / TO-BE. Hay descripción narrativa del proceso (p.25-26) pero sin notación BPMN 2.0 | — |
| **UML Casos de uso** | **SÍ** — 9 diagramas | Panel control, Usuarios, Empleado, Lotes, Insumos, Actividades/Asignaciones, Producción/Cosecha, Reportes, Administración — elaborados en **Lucidchart** | Anexos 9-17 (p.53-57), descritos p.28-30 |
| **UML otros** | No detectado | No hay diagrama de clases, secuencia o actividades UML — solo casos de uso | — |
| **ER / Modelo relacional** | **SÍ** | Diagrama relacional (Apéndice 2, p.101) + **12 tablas** documentadas con diccionario | Anexos 18 (p.58) + Apéndice 2 |
| **Diccionario de datos** | **SÍ — muy completo** | Tablas 7-18: `usuarios`, `empleado`, `control_asistencia`, `permisos_faltas`, `lotes`, `insumos`, `actividades`, `asignaciones`, `plagas_enfermedades`, `producción`, `análisis`, `administración` — con columna, tipo (int, nvarchar, enum, timestamp), nulabilidad, default | p.58-63 |
| **Prototipos / UI** | **SÍ** | Interfaces responsive Bootstrap + CSS/JS — capturas por módulo | Anexo 19 (p.64-74) |
| **Pruebas** | **SÍ** | Tablas 19-27: pruebas por módulo (login con credenciales vacías/incorrectas/correctas, CRUD empleados/lotes/insumos, asignaciones, producción, reportes, backup/restore) | Anexo 20 (p.75-82) |
| **Manuales** | **SÍ** | Manual técnico (p.83-90) y manual de usuario (p.91-97) + acta entrega (p.98) | Anexos 21-23 |

---

## 6. Vacíos de seguridad y LOPDP

### Seguridad técnica

| Hallazgo | Estado tesis | Riesgo |
|---|---|---|
| Hash de contraseñas | RNF-01 promete "encriptación de contraseñas" pero **diccionario define `contraseña nvarchar(255)` sin algoritmo**; 0 menciones de `hash`, `bcrypt`, `Argon2`, `salt` en todo el PDF (búsqueda: hash=0) | **Crítico** — probable almacenamiento en claro o hash débil |
| Gestión de sesión | Solo "inicio de sesión" narrativo; sin timeout, sin regeneración de sesión, sin bloqueo por intentos fallidos | Medio |
| Validación / inyección | No menciona validación de entrada, prepared statements, CSRF, XSS | Crítico |
| Transporte | Menciona SSL/hosting como concepto (p.12) pero no como requisito implementado | Medio |
| Auditoría y logs | Sin trazabilidad de acciones por usuario | Bajo |
| Backup/restore | Existe (módulo administración) pero **sin cifrado del dump ni control de acceso al archivo** | Medio |
| Recuperación de clave | CU5 "Restablecer clave por correo si está configurado" — sin token expirable ni flujo seguro descrito | Medio |

### LOPDP (Ley Orgánica de Protección de Datos Personales, 2021)

- **Marco legal citado correctamente:** Art. 37 LOPDP (p.16) + referencia en bibliografía — pero **solo como declaración genérica**.
- **Sin implementación:** No hay aviso de privacidad, base de legitimación, consentimiento, derechos ARCO (acceso/rectificación/eliminación), minimización (se almacena cédula, celular, dirección sin justificación de retención), plazo de conservación, registro de tratamiento, ni anonimización.
- **Datos sensibles del personal:** `empleado.cedula`, `celular`, `direccion` + `control_asistencia` — requieren tratamiento LOPDP; el sistema los expone en reportes exportables y envíos por Gmail sin cifrado.
- **Envío por Gmail (PDF/Excel):** Funcionalidad destacada pero sin evaluación de transferencia segura de datos personales.

**Qué debe añadirse para cumplir IS2:** hashing con `password_hash`/`bcrypt`, política de contraseñas, control de sesiones, validación y PDO/prepared, CSRF tokens, RBAC, logs de auditoría, aviso LOPDP + consentimiento, minimización y seudonimización de cédula, cifrado de backups, y flujo de recuperación con token expirable por correo.

---

## 7. Evaluación de sencillez para rediseño (escala: Muy simple / Simple / Media / Compleja)

**Veredicto: SIMPLE — Muy favorable para rediseño IS2**

| Criterio | Evaluación |
|---|---|
| **Dominio** | Agricultura familiar 6 ha, proceso lineal y bien acotado (7 etapas: preparación → siembra → riego → fertilización → plagas → monitoreo → cosecha). Sin integración con terceros, sin IoT, sin facturación. **Ideal para BPMN.** |
| **Número de entidades** | 12 tablas — tamaño manejable. Relaciones claras: empleado ↔ asistencia/permisos, lote ↔ actividad ↔ asignación ↔ insumo ↔ plaga ↔ producción. Sin relaciones complejas muchos-a-muchos descontroladas. |
| **Lógica de negocio** | CRUD + asignaciones + reportes con filtros. Sin workflow con estados complejos ni cálculos financieros pesados. La asignación actividad-empleado-lote-insumo es el único flujo transaccional. |
| **Stack original** | PHP/MySQL/Bootstrap — port directo a Laravel/Symfony o Node; sin dependencias exóticas. Hostinger + XAMPP = despliegue trivial. |
| **Documentación base** | Diccionario de datos + RF/RNF + casos de uso + UI mockups + pruebas ya existen — se reutiliza ~70% para el rediseño sin relevar desde cero. |
| **Población** | 1 usuario real — sin concurrencia, sin escalamiento; permite foco en calidad del diseño sobre performance. |
| **BPMN faltante** | Debe crearse desde cero pero el proceso está narrado (p.25-27, ficha observación p.51) — se modela en 2-3 diagramas en 1 tarde. |
| **Riesgos de rediseño** | Bajo. Único riesgo: ampliar RBAC y LOPDP exige decisiones de diseño (matriz permisos, flujos de consentimiento) pero son extensiones, no refactors del núcleo. |

**Esfuerzo estimado para llevarla a estándar IS2 (4+ módulos + auth roles + BPMN + UML + ER + LOPDP + pruebas):**

- BPMN AS-IS/TO-BE (3 diagramas) + UML retoque (añadir clase y secuencia de asignación/producción): **1-2 días**
- ER refinado (normalización, FKs, índices) + corrección diccionario: **0.5 días** (base ya sólida)
- Auth + RBAC (2-3 roles, middleware, matriz permisos): **2-3 días**
- Hardening seguridad (hash, validación, CSRF, logs, backup cifrado): **1-2 días**
- LOPDP (aviso, consentimiento, derechos ARCO, minimización): **1 día**
- Suite pruebas (unitarias + integración + E2E de los 10 módulos): **2 días**

**Total: ~7-10 días de trabajo estudiante IS2** — claramente por debajo de tesis con 20+ tablas o integraciones externas.

### Comparado con el resto del banco (10 tesis)

Es la **más simple** junto a Sicha (454 ha? no, otra escala) — pero Vallejo es más simple que Portocarrero, Miranda o Valdivieso por su alcance de 6 ha y proceso sin comercialización. Por eso es **candidata #1 para un rediseño rápido y completo que cumpla todos los entregables de IS2 sin deuda técnica.**

---

## 8. Índice extraído (p.ix — p.9)

```
1. INTRODUCCIÓN (p.1) — antecedentes, planteamiento, justificación (p.3-5 con detalle de 10 módulos), delimitación, objetivos
2. MARCO TEÓRICO (p.7-17) — estado del arte (Ramírez 2022, Zamora 2022...), bases científicas (cultivo, siembra, riego...), sistema web/PHP/HTML/CSS/JS/MySQL/Bootstrap, marco legal LOPDP + software libre
3. MATERIALES Y MÉTODOS (p.18-24) — enfoque cualitativo descriptivo/documental no experimental, XP 5 fases, recursos (hardware i5/16GB/512GB, presupuesto $916), método inductivo/deductivo, entrevista + observación, sin muestreo (n=1)
4. RESULTADOS (p.25-33) — entrevista, observación, necesidades, RF/RNF, diseño UML/BD/UI, implementación y pruebas piloto por módulo, manuales y entrega
5. DISCUSIÓN (p.34-35)
6. CONCLUSIONES Y RECOMENDACIONES (p.36)
BIBLIOGRAFÍA (p.38-43)
ANEXOS (p.44-98) — 23 anexos: recursos, entrevistas, fichas, RF/RNF, 9 casos de uso, diccionario 12 tablas, UI, pruebas, manuales
APÉNDICES (p.100-101) — cronograma + diagrama BD
```

---

## 9. Recomendación

**APTA para rediseño IS2 — Prioridad ALTA.**

- Cumple sobrado el mínimo de 4 módulos (10 reales).
- Ya trae ER + UML casos de uso + diccionario + pruebas + manuales — el rediseño es **evolutivo, no desde cero**.
- Únicos entregables a crear: **BPMN**, **RBAC multi-rol**, **hardening seguridad (hash/CSRF/validación)** y **capa LOPDP operativa**.
- Dominio agrícola acotado, sin integraciones, ideal para demostrar BPMN → UML → ER → implementación → pruebas en ciclo XP.
- Corregir inconsistencia Freire/Quinteros y completar metadatos de BD (FKs explícitas en diagrama).

---

*Extracción verificada con `pymupdf` — texto íntegro de portada, resumen, índice, p.4-6 (módulos), p.52-53 (RF/RNF), p.58-63 (diccionario), p.101 (ER) y búsqueda full-text de BPMN/UML/LOPDP/seguridad/hash.*
