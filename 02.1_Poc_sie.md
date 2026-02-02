## **Prueba de Concepto (PoC) del hipotético Sistema de Información Escolar (SiE)**
## Version 0.1

Octubre de 2025

dr. Jesús Zavala Ruiz

### **Componentes de la Infraestructura**

**Base del Sistema:**
- **Rocky Linux**: Sistema operativo empresarial (servidor base para todos los servicios)

### **① FreeIPA** (Autenticación y Directorio)
- Sistema de gestión de identidades centralizado
- Directorio LDAP institucional
- Single Sign-On (SSO)
- Control de acceso basado en roles:
  - Administradores
  - Aspirantes
  - Alumnos
  - Egresados
  - Profesores
  - Directivos
  - Coordinadores
  - Asistentes

### **② PostgreSQL** (Base de Datos)
- Sistema gestor de base de datos del SiE
- Almacena toda la información operativa:
  - **Planes de estudio**: estructura, créditos, objetivos, perfil de egreso
  - **Programas de estudio (UEA)**: seriación, prerrequisitos, contenidos, bibliografía, modalidades
  - **Aspirantes**: datos personales y académicos 
  - **Egresados**: datos de titulación, seguimiento, empleabilidad
  - **Alumnos**: datos personales y académicos 
  - **Profesores**: cargas académicas, grupos
  - **Directivos**: cargo, rol
  - **Admisión**: aspirantes, proceso de selección
  - **Inscripciones**: trimestres, UEAs cursadas, calificaciones
  - **Reinscripciones**: trimestres, UEAs cursadas, calificaciones
  - **Salones**: capacidad, condiciones
  - **Grupos**: lista de grupo, salón, horario, profesor
  - **Evaluaciones** globales, de recuperación y colegiadas
  - **Actas**: lista de alumnos, calificaciones, sinodales, firmas
  - **Seriación**: prerequisitos entre UEAs
  - **Historial**: versiones de planes y programas
  - **Trámites**: solicitudes, seguimiento, bitácora
  - **Credenciales**: registro de credenciales emitidas, fotografías, vigencias
  - **Kardex**: historial académico, avance curricular


### **③ Mayan EDMS** (Gestión Documental)
Sistema de gestión de documentos electrónicos enfocado en:

**Documentos Académicos:**
- Planes de estudio (documentos oficiales)
- Programas de estudio (por UEA)

**Documentos de Admisión:**
- Solicitudes de ingreso
- Documentos probatorios del aspirante
- Resultados de proceso de selección
- Cartas de aceptación
- Fotografías para credencial inicial

**Documentos de Evaluación:**
- **Actas de Evaluación Global** (calificaciones ordinarias del trimestre)
- **Actas de Evaluación de Recuperación** (exámenes de recuperación)
- **Actas de Evaluación de Revisión** (revisiones de examen) y documentos de justificación de calificaciones

**Documentos de Trámites Escolares:**
- Solicitudes de reinscripción
- Cambios de plan de estudios
- Movilidad estudiantil
- Bajas temporales y definitivas
- Equivalencias y revalidaciones
- Servicio social y prácticas profesionales
- Fotografías para reposición de credencial
- Documentos de soporte para reposición

**Documentos de Trámites de Profesores:**
- Contratos y nombramientos
- Asignación de carga académica
- Programas operativos por grupo
- Reportes de evaluación
- Fotografías para credencial

**Documentos de Egresados y Titulación:**
- Expediente de titulación completo
- Actas de examen profesional
- Títulos y certificados
- Cédula profesional
- Documentos de seguimiento de egresados
- Encuestas de empleabilidad

**Documentos Oficiales:**
- Constancias (estudios, calificaciones, servicio social)
- Historiales académicos oficiales
- Kardex
- Credenciales (respaldo fotográfico y diseños)

**Características:**
- Versionado automático de documentos
- Workflow de aprobación documental
- Firma electrónica
- Búsqueda avanzada
- Control de acceso por documento
- OCR para documentos escaneados

### **④ iDempiere** (Sistema Escolar - SiE)
Sistema ERP adaptado como **sistema de gestión escolar completo**:

#### **Módulo de Admisión**
- Registro de aspirantes
- Gestión del proceso de selección
- Examen de admisión
- Asignación de lugares
- Generación de documentos de aceptación
- Reportes estadísticos de admisión

#### **Módulo de Inscripción**
- Alta de nuevos alumnos
- **Credencialización inicial**:
  - Captura de fotografía digital
  - Validación de formato y calidad de imagen
  - Generación de credencial de alumno
  - Datos de credencial: fotografía, matrícula, carrera, vigencia, código QR
  - Registro en base de datos
  - Almacenamiento de fotografía en **Mayan EDMS**
  - Notificación para entrega física
  - Impresión de credencial
- Portal de inscripción en línea
- Validación de seriación y prerequisitos
- Control de cupo por grupo
- Validación de carga de créditos (mínima/máxima)
- Asignación automática/manual de grupos
- Generación de horarios personalizados
- Tira de materias
- Comprobante de inscripción

#### **Módulo de Reinscripción**
- Validación de estatus del alumno
- Control de periodos de reinscripción
- Prioridad por avance curricular
- Verificación de adeudos de cuotas
- Actualización de datos personales
- Selección de UEAs del siguiente trimestre
- Confirmación de reinscripción

#### **Módulo de Evaluación**
- **Generación de actas**:
  - Acta de Evaluación Global
  - Acta de Evaluación de Recuperación
  - Acta de Evaluación de Revisión
- **Validación de actas** por coordinación
- **Captura de calificaciones** por profesores
- Cierre de trimestre
- Cálculo de promedios (trimestral, acumulado)
- Historial de calificaciones
- Estadísticas de aprovechamiento por UEA/grupo
- Alertas de bajo rendimiento

#### **Módulo de Grupos y Horarios**
- **Creación de grupos** por UEA y trimestre
- **Asignación de profesores** a grupos
- **Programación de horarios**:
  - Asignación de salones
  - Días y horarios de clase
  - Validación de traslapes
- **Control de capacidad** de grupos
- **Gestión de listas** de asistencia
- Reprogramación y cambios de horario
- Optimización de uso de espacios

#### **Módulo de Trámites Escolares**
- **Solicitudes en línea**:
  - Constancias
  - Historiales académicos
  - Certificados
  - Cambio de plan
  - Equivalencias
  - Baja temporal/definitiva
  - Reingreso
  - **Reposición de credencial**:
    - Registro de motivo (pérdida, robo, deterioro)
    - Invalidación de credencial anterior
    - Captura de nueva fotografía (si aplica)
    - Generación de nueva credencial
    - Historial de reposiciones
    - Notificación de disponibilidad
    - Control de pagos (si aplica)
- **Workflow de aprobación** multi-nivel
- **Seguimiento de estatus** en tiempo real
- Notificaciones automáticas
- Generación de documentos oficiales
- Bitácora de trámites
- Reportes de gestión

#### **Módulo de Trámites de Profesores**
- **Gestión de plantilla docente**
- **Asignación de carga académica**:
  - Grupos asignados
  - Horas frente a grupo
  - Validación de carga máxima
- **Programas operativos** por grupo
- Solicitudes de:
  - Cambio de horario
  - Sustitución de profesor
  - Licencias y permisos

#### **Módulo de Egresados y Titulación**
- **Registro de egreso**:
  - Detección automática al completar créditos
  - Cambio de estatus: Alumno → Egresado 
  - Fecha de egreso
  - Promedio final
  - Modalidad de titulación elegida
- **Proceso de titulación completo**:
  - Solicitud de examen profesional
  - Validación de requisitos
  - Asignación de sinodales
  - Programación de fecha de examen
  - Registro de acta de examen
  - Resultado de evaluación
  - Cambio de estatus: Egresado → Titulado 
  - Generación de título → **Mayan EDMS**
  - Trámite de cédula profesional
  - Ceremonia de titulación
- **Reportes y estadísticas**:
  - Tasa de titulación por generación
  - Tiempo promedio de titulación
  - Empleabilidad por carrera
  - Áreas de inserción laboral
  - Nivel salarial promedio
  - Satisfacción de empleadores

#### **Portal de Alumnos**
- Consulta de calificaciones
- Avance curricular con gráficos
- Horario personalizado
- Inscripción/reinscripción en línea
- Solicitud de trámites
- Descarga de documentos
- Mensajes y notificaciones
- Solicitud de reposición de credencial
- Consulta de estatus de credencial

#### **Portal de Profesores**
- Consulta de grupos asignados
- Captura de calificaciones
- Listas de asistencia
- Programas operativos
- Comunicación con alumnos
- Solicitud de reposición de credencial
- Consulta de carga académica

#### **Portal de Egresados**
- Actualización de datos laborales
- Consulta de historial académico
- Solicitud de documentos
- Registro en bolsa de trabajo
- Acceso a educación continua
- Respuesta a encuestas de seguimiento
- Credencial de egresado
- Red de contactos (alumni)

#### **Reportes y Analítica**
- Dashboard institucional
- Estadísticas de inscripción por trimestre
- Índices de aprobación/reprobación
- Deserción y retención
- Carga académica de profesores
- Ocupación de grupos y salones
- Eficiencia terminal
- Tasa de titulación
- Tiempo promedio de titulación
- Empleabilidad de egresados
- Seguimiento de trayectorias
- Reportes regulatorios

**Extensibilidad:**
- *Nota: El sistema puede extenderse al sistema financiero (colegiaturas, pagos, becas) y administrativo (recursos humanos, nómina, activos) institucional*

---

## **Proceso de Integración (Orden de Implementación)**

### **Secuencia de Integración**

```
┌─────────────────────────────────────────────────────────────┐
│              PROCESO DE INTEGRACIÓN DEL SiE                 │
└─────────────────────────────────────────────────────────────┘

   ┌──────────────┐
   │   FASE 1     │
   │   FreeIPA    │  ← Primero: Autenticación y directorio
   └──────┬───────┘
          │
          ▼
   ┌──────────────┐
   │   FASE 2     │
   │ PostgreSQL   │  ← Segundo: Base de datos
   └──────┬───────┘
          │
          ▼
   ┌──────────────┐
   │   FASE 3     │
   │  Mayan EDMS  │  ← Tercero: Gestión documental
   └──────┬───────┘
          │
          ▼
   ┌──────────────┐
   │   FASE 4     │
   │  iDempiere   │  ← Cuarto: Sistema escolar
   └──────────────┘
```

### **FASE 1: Implementación de FreeIPA** (1 semana)

**Objetivos:**
- Establecer sistema de autenticación centralizado
- Crear estructura de directorio LDAP
- Definir roles y permisos

**Actividades:**
1. Instalación de FreeIPA en Rocky Linux
2. Configuración de dominio institucional
3. Creación de estructura organizacional:
   - Unidades (División, Departamento, Coordinación)
   - Grupos de usuarios (Alumnos, Profesores, Administrativos, Egresados)
4. Definición de políticas de contraseñas
5. Configuración de certificados SSL
6. Pruebas de autenticación

**Entregables:**
- Servidor FreeIPA operativo
- Directorio LDAP estructurado
- Documentación de configuración
- Manual de administración de usuarios



### **FASE 2: Implementación de PostgreSQL** (1 semana)

**Objetivos:**
- Instalar y configurar base de datos
- Crear esquema del SiE
- Implementar validaciones y constraints

**Actividades:**
1. Instalación de PostgreSQL en Rocky Linux
2. Configuración de seguridad y acceso
3. Creación de base de datos `SiE_uam`
4. Implementación del modelo de datos:
   - Tablas de Planes de estudio
   - Tablas de Alumnos y Egresados
   - Tablas de Inscripciones y Evaluaciones
   - Tablas de Grupos y Horarios
   - Tablas de Trámites
   - Tablas de Credencialización (registro, fotografías, vigencias)
   - Tablas de Titulación
5. Creación de índices para optimización
6. Implementación de triggers y procedimientos almacenados
7. Configuración de respaldos automáticos
8. **Integración con FreeIPA**: Autenticación de usuarios de BD

**Entregables:**
- Base de datos PostgreSQL operativa
- Esquema completo del SiE implementado
- Scripts de creación y migración
- Documentación de modelo de datos
- Plan de respaldos configurado



### **FASE 3: Implementación de Mayan EDMS** (2 semanas)

**Objetivos:**
- Instalar sistema de gestión documental
- Configurar tipos de documentos
- Establecer workflows de aprobación

**Actividades:**
1. Instalación de Mayan EDMS en Rocky Linux
2. **Integración con FreeIPA**: SSO y control de acceso
3. **Conexión con PostgreSQL**: Uso de BD para metadatos
4. Configuración de tipos de documentos:
   - Planes de estudio
   - Programas de UEA
   - Actas de evaluación (3 tipos)
   - Documentos de admisión (incluyendo fotografías)
   - Documentos de trámites (incluyendo reposición de credencial)
   - Documentos de egresados y titulación
   - Constancias y títulos
   - Credenciales (fotografías y diseños)
5. Definición de metadatos por tipo de documento
6. Configuración de workflows:
   - Aprobación de actas
   - Validación de constancias
   - Proceso de titulación
7. Configuración de permisos por rol
8. Implementación de firma digital
9. Pruebas de carga y versionado

**Entregables:**
- Mayan EDMS operativo
- Tipos de documentos configurados
- Workflows implementados
- Manual de usuario
- Integración con FreeIPA y PostgreSQL completada



### **FASE 4: Implementación de iDempiere (SiE)** (6 semanas)

**Objetivos:**
- Instalar y configurar iDempiere
- Desarrollar/adaptar módulos del SiE
- Integrar con componentes previos

**Actividades:**

**Semanas 1-2: Instalación y Configuración Base**
1. Instalación de iDempiere en Rocky Linux
2. **Integración con FreeIPA**: SSO institucional
3. **Conexión con PostgreSQL**: Configuración de acceso a BD del SiE
4. **Integración con Mayan EDMS**: APIs para gestión documental
5. Configuración de organización y roles

**Semanas 3-4: Módulo de Admisión (incluye Credencialización inicial)**
1. Desarrollo/adaptación del módulo de Admisión
2. Proceso de selección y aceptación
3. **Subproceso de Credencialización inicial**:
   - Captura de fotografía digital
   - Validación de imagen
   - Generación de credencial
   - Envío de foto a Mayan EDMS
   - Registro en PostgreSQL
4. Alta de nuevos alumnos
5. Interfaces de captura y consulta
6. Pruebas integrales

**Semanas 5-6: Módulos de Inscripción y Reinscripción**
1. Desarrollo/adaptación módulo de Inscripción
2. Desarrollo/adaptación módulo de Reinscripción
3. Validación de seriación y prerequisitos
4. Generación de horarios
5. Pruebas de validación

**Semanas 7-8: Módulos de Evaluación y Grupos**
1. Desarrollo/adaptación módulo de Evaluación
2. Generación automática de actas → Mayan EDMS
3. Desarrollo/adaptación módulo de Grupos y Horarios
4. Validación de traslapes y capacidades
5. Listas de asistencia

**Semanas 9-10: Módulo de Trámites (incluye Reposición de Credencial)**
1. Desarrollo/adaptación módulo de Trámites Escolares
2. **Subproceso de Reposición de Credencial**:
   - Solicitud con motivo
   - Invalidación de credencial anterior
   - Nueva fotografía (si aplica)
   - Generación de nueva credencial
   - Historial de reposiciones
3. Workflows de aprobación
4. Desarrollo/adaptación módulo de Trámites de Profesores
5. Generación de documentos → Mayan EDMS

**Semanas 11-12: Módulo de Egresados y Titulación + Portales**
1. Desarrollo/adaptación módulo unificado de Egresados y Titulación:
   - Registro de egreso
   - Proceso completo de titulación
   - Seguimiento laboral
   - Encuestas
   - Servicios para egresados
2. Desarrollo de Portal de Alumnos
3. Desarrollo de Portal de Profesores
4. Desarrollo de Portal de Egresados
5. Implementación de dashboards y reportes
6. Pruebas integrales end-to-end
7. Capacitación a usuarios

**Entregables:**
- iDempiere (SiE) completamente operativo
- Todos los módulos implementados y probados
- Integración completa con FreeIPA, PostgreSQL y Mayan EDMS
- Portales web funcionales
- Manuales de usuario por rol
- Documentación técnica completa



## **Arquitectura de Integración Final**

```
                         ┌─────────────┐
                         │  FreeIPA    │
                         │(Login/LDAP) │
                         │             │
                         │ - Alumnos   │
                         │ - Egresados │
                         │ - Profesores│
                         │ - Personal  │
                         └──────┬──────┘
                                │
                   ┌────────────┴────────────┐
                   │                         │
                   ▼                         ▼
             ┌───────────┐            ┌─────────────┐
             │iDempiere  │◄───────────│ Mayan EDMS  │
             │   (SiE)   │    API     │ (Documentos)│
             │           │            │             │
             │ Módulos:  │            │ Actas:      │
             │ -Admisión*│            │ -Global     │
             │  +Credenc │            │ -Recuperac. │
             │ -Inscr.   │            │ -Revisión   │
             │ -Reinscr. │            │             │
             │ -Evaluac. │            │ Docs:       │
             │ -Grupos   │            │ -Planes     │
             │ -Horarios │            │ -Programas  │
             │ -Trámites*│            │ -Admisión   │
             │  +Repos.  │            │ -Trámites   │
             │ -Egresados│            │ -Egresados  │
             │  +Titul.  │            │ -Títulos    │
             │           │            │ -Fotos      │
             └─────┬─────┘            └──────┬──────┘
                   │                         │
                   │    ┌───────────┐        │
                   └────►PostgreSQL │◄───────┘
                        │  (Datos)  │
                        │           │
                        │ Tablas:   │
                        │ -Alumnos  │
                        │ -Egresados│
                        │ -Credenc. │
                        │ -Titul.   │
                        └───────────┘

* Admisión incluye credencialización inicial
* Trámites incluye reposición de credencial
```



## **Casos de Uso Actualizados**

### **Caso 1: Admisión con Credencialización Inicial**

1. Aspirante completa proceso de admisión vía **FreeIPA**
2. **iDempiere** - Módulo de Admisión:
   - Registra aceptación del aspirante
   - Genera matrícula
   - Solicita carga de fotografía digital
3. Alumno carga fotografía en formato requerido
4. Sistema valida calidad y formato de imagen
5. **iDempiere** genera credencial de alumno:
   - Fotografía
   - Nombre completo
   - Matrícula
   - Carrera
   - Vigencia (4 años)
   - Código QR para verificación
6. Fotografía se envía a **Mayan EDMS**
7. Datos de credencial se registran en **PostgreSQL**
8. Sistema notifica al alumno para recoger credencial física
9. Credencial se imprime y entrega en servicios escolares

### **Caso 2: Reposición de Credencial (Trámite Escolar)**

**Por pérdida o robo:**
1. Alumno/Profesor accede al portal vía **FreeIPA**
2. En **Trámites Escolares/de Profesores**, selecciona "Reposición de Credencial"
3. Sistema presenta formulario:
   - Motivo: Pérdida/Robo/Deterioro
   - Descripción de circunstancias
   - Opción de cargar nueva foto (si desea actualizar)
4. **iDempiere** registra solicitud
5. Sistema invalida credencial anterior en **PostgreSQL**
6. Si carga nueva foto → se envía a **Mayan EDMS**
7. **iDempiere** genera nueva credencial con:
   - Nueva fotografía (si aplica) o la existente
   - Mismos datos personales actualizados
   - Nueva fecha de vigencia
   - Nuevo código QR
8. Historial de reposiciones se actualiza en **PostgreSQL**
9. Notificación de disponibilidad
10. Usuario recoge nueva credencial

**Por deterioro:**
1. Similar al flujo anterior
2. Usuario puede mantener fotografía actual
3. Entrega credencial deteriorada al recoger la nueva

### **Caso 3: Ciclo Completo - Alumno a Egresado Titulado**

**Admisión (con credencialización):**
1. Aspirante aceptado → alta como alumno
2. **Credencial inicial** generada en proceso de admisión
3. Fotografía en **Mayan EDMS**, datos en **PostgreSQL**

**Durante estudios:**
4. Inscripciones trimestrales
5. Evaluaciones → actas en **Mayan EDMS**
6. Si pierde credencial → reposición vía **Trámites**
7. Progreso académico en **PostgreSQL**

**Al completar créditos:**
8. Sistema detecta cumplimiento del plan
9. **iDempiere** - Módulo Egresados y Titulación:
   - Cambia estatus a "Pasante"
   - Habilita proceso de titulación
   - Credencial de alumno permanece vigente

**Proceso de titulación:**
10. Alumno solicita titulación vía portal
11. Sistema crea expediente en **Mayan EDMS**
12. Workflow de titulación:
    - Validación de requisitos
    - Asignación de sinodales
    - Programación de fecha
    - Registro de acta de examen
    - Resultado aprobatorio
13. **iDempiere** genera título → **Mayan EDMS**
14. Sistema cambia estatus a "Egresado Titulado"
15. Credencial de alumno se invalida automáticamente
16. Datos actualizados en **PostgreSQL**

**Como egresado:**
17. Acceso a Portal de Egresados habilitado
18. Puede solicitar credencial de egresado (trámite)
19. Actualiza datos laborales
20. Responde encuestas de seguimiento
21. Accede a servicios para egresados

### **Caso 4: Profesor - Alta con Credencial**

1. Recursos Humanos registra nuevo profesor vía **FreeIPA**
2. **iDempiere** - Módulo Trámites de Profesores:
   - Solicita fotografía digital
   - Captura datos complementarios
3. Fotografía se envía a **Mayan EDMS**
4. Sistema genera credencial de profesor:
   - Fotografía
   - Nombre
   - Número de empleado
   - División/Departamento
   - Vigencia
   - Código QR
5. Registro en **PostgreSQL**
6. Notificación para recoger credencial

**Reposición:**
7. Profesor solicita reposición vía portal
8. Mismo flujo que alumnos en **Trámites de Profesores**
9. Nueva credencial generada



## **Cronograma Total de Implementación**

| Fase | Componente | Duración | Semanas Acumuladas |
||--|-|-|
| 1 | FreeIPA | 2-3 semanas | 3 |
| 2 | PostgreSQL | 3-4 semanas | 7 |
| 3 | Mayan EDMS | 4-5 semanas | 12 |
| 4 | iDempiere (SiE) | 8-12 semanas | 24 |
| **TOTAL** | | **17-24 semanas** | **~6 meses** |

*Nota: Se puede agregar 2-4 semanas adicionales para pruebas integrales, capacitación y puesta en producción.*



## **Resumen de la Reorganización**

### **Credencialización Integrada:**
- **Emisión inicial** → Parte del módulo de **Admisión**
- **Reposición** → Parte del módulo de **Trámites Escolares/de Profesores**
- No es módulo independiente, sino funcionalidad transversal

### **Egresados y Titulación Unificados:**
- **Un solo módulo** que gestiona:
  - Registro de egreso
  - Proceso completo de titulación
  - Seguimiento de egresados
  - Servicios y encuestas
- Visión integral del ciclo post-egreso



Esta arquitectura reorganizada mantiene la claridad funcional mientras refleja correctamente la estructura modular del SiE, con credencialización como proceso integrado y egresados/titulación como módulo unificado.
