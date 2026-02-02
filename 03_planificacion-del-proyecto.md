## Planificación del Proyecto Prueba de Concepto del Sistema de Información Escolar (SiE), basada en la PMBOK® Guide 8

Dr. Jesús Zavala Ruiz

1 de febrero de 2026

### Introducción

El presente documento constituye una guía práctica para la planificación de proyectos de desarrollo de software en entornos académicos, elaborada con base en *A Guide to the Project Management Body of Knowledge (PMBOK® Guide)* — Eighth Edition (Project Management Institute [PMI], 2025). Su propósito es traducir los principios y dominios de desempeño del estándar internacional a un caso de estudio realista y contextualizado: la Prueba de Concepto (PoC) del Sistema de Información Escolar (SiE) para la Unidad Iztapalapa de la Universidad Autónoma Metropolitana.

La planificación efectiva de proyectos tecnológicos en instituciones educativas públicas enfrenta desafíos singulares: limitaciones presupuestales, necesidad de soberanía tecnológica, curvas de aprendizaje en equipos emergentes y la obligación de preservar el conocimiento institucional como activo intangible. Frente a estos retos, el PMBOK Guide 8th Edition ofrece un marco flexible que reconoce que:

> "El *tailoring* es la adaptación deliberada de enfoques, procesos y artefactos de gestión de proyectos para satisfacer las necesidades específicas de un proyecto" (PMI, 2025, p. 104, traducción propia).

Esta guía aplica dicho principio de adaptación deliberada al contexto específico de una fábrica de software educativa, donde 30 alumnos destinan 11 horas semanales a la construcción de una arquitectura tecnológica integral basada en software libre. La PoC del SiE integra seis componentes interdependientes organizados jerárquicamente —desde Rocky Linux 9.x como plataforma base (Nivel 0) hasta iDempiere 9.x como sistema ERP escolar (Nivel 4)—, validando la viabilidad técnica, operativa y económica de reemplazar sistemas legacy propietarios por una solución autónoma, sostenible y alineada con los procesos académicos específicos de la UAM.

El documento se estructura en dos secciones fundamentales. La primera adapta los siete dominios de desempeño del PMBOK Guide (gobernanza, alcance, cronograma, finanzas, partes interesadas, recursos y riesgos) al caso del SiE, incorporando citas textuales verificadas del estándar con sus traducciones al español y referencias al estudio de factibilidad institucional. La segunda sección, como Anexo 1, presenta un plan operativo detallado de 8 semanas que distribuye las 2,640 horas-hombre totales del equipo educativo en hitos técnicos secuenciales, respetando las dependencias arquitectónicas y maximizando la transferencia de conocimiento mediante documentación UML como activo institucional.

Esta guía no pretende ser un manual prescriptivo, sino una *demostración de cómo los principios universales de gestión de proyectos pueden materializarse en contextos educativos con recursos limitados pero alto potencial transformador*. Al integrar rigor metodológico con pragmatismo técnico, busca servir de apoyo a la UEA Ingeniería de Software de la Licenciatura en Computación y como referente para organizaciones que aspiran a recuperar su autonomía tecnológica mediante el desarrollo interno de sistemas críticos, formando simultáneamente capital humano especializado en arquitecturas de software libre empresarial.

### 1. Arquitectura del Proyecto

El proyecto consiste en el desarrollo de una PoC de un hipotético SiE mediante una arquitectura de software libre compuesta por seis componentes interdependientes organizados en niveles jerárquicos:

-   **Nivel 0:** Rocky Linux 9.x (sistema operativo base con SELinux enforcing y LUKS2 para cifrado)
-   **Nivel 1:** FreeIPA (autenticación centralizada LDAP/Kerberos)
-   **Nivel 2:** PostgreSQL 15 (base de datos transaccional ACID)
-   **Nivel 3:** Apache Tomcat 10 + Mayan EDMS 4.x (contenedor Java y gestión documental con cumplimiento LGPD mexicana)
-   **Nivel 4:** iDempiere 9.x (ERP escolar adaptado mediante Application Dictionary)

La secuencia de integración sigue una lógica de dependencias técnicas fundamentales que minimiza riesgos operativos:

> "La secuencia de integración propuesta —FreeIPA → PostgreSQL → iDempiere → Mayan EDMS— responde a una lógica de dependencias técnicas fundamentales: el sistema de autenticación debe existir antes de que otros componentes puedan operar con identidades gestionadas; la base de datos debe estar disponible antes de que los sistemas puedan almacenar información estructurada" (Zavala, 2026, p. 12).

Rocky Linux 9.x constituye la plataforma base óptima por su condición de *rebuild* binariamente compatible con RHEL:

> "Rocky Linux está esencialmente construido a partir de la misma base de código fuente que Red Hat Enterprise Linux, pero con el branding de Red Hat y los requisitos de suscripción eliminados" (Smyth, 2023, p. 9, traducción propia).

Esta compatibilidad garantiza estabilidad empresarial sin costo de licenciamiento comercial (\~\$300,000 MXN/año para 5 servidores), preservando soberanía tecnológica institucional:

> "La elección de Rocky Linux 9.x para la PoC representa una decisión estratégica de soberanía tecnológica para instituciones públicas mexicanas. A diferencia de soluciones comerciales que imponen dependencia de proveedores únicos, Rocky Linux permite a la UAM ejercer control pleno sobre su infraestructura tecnológica crítica" (Zavala, 2026, p. 34).

### 2. Principios Fundamentales

La planificación se rige por el principio de *"Construir una Cultura Empoderada"* (*Build an Empowered Culture*), crítico para entornos educativos donde el capital humano es el recurso principal:

> "Construir una cultura empoderada requiere crear un entorno donde los miembros del equipo sean confiados, respetados y dotados de autonomía para tomar decisiones dentro de sus áreas de especialización" (PMI, 2025, p. 53, traducción propia).

Para el SiE, el *tailoring* (adaptación deliberada) es esencial dada la naturaleza híbrida del proyecto (componentes predictivos para arquitectura base y adaptativos para configuración de procesos académicos):

> "El *tailoring* es la adaptación deliberada de enfoques, procesos y artefactos de gestión de proyectos para satisfacer las necesidades específicas de un proyecto" (PMI, 2025, p. 104, traducción propia).

### 3. Planificación por Dominios de Desempeño

#### 3.1. Dominio de Desempeño de Gobernanza (*Governance Performance Domain*)

**Actividades clave:**

\- Elaborar acta de proyecto que autorice formalmente la PoC del SiE bajo la supervisión del Coordinador de Sistemas Escolares.\
- Definir modelo de gobernanza considerando la integración con la estructura administrativa universitaria y la gobernanza comunitaria neutral de los componentes de software libre.

> "El acta de proyecto es un documento emitido por el iniciador o patrocinador del proyecto que autoriza formalmente la existencia de un proyecto y proporciona al gestor del proyecto la autoridad para aplicar los recursos organizacionales a las actividades del proyecto" (PMI, 2025, p. 125, traducción propia).

**Entregable práctico para el SiE:** Acta de proyecto que incluya:\
- Justificación basada en el estudio de factibilidad (VAN positivo de 19,987 miles de MXN en 10 años)\
- Objetivos medibles: validación técnica de los seis componentes en secuencia progresiva (Nivel 0 → Nivel 4) en 8 semanas\
- Presupuesto autorizado inicial para la PoC (hardware virtualizado y capacitación)\
- Patrocinador institucional: Coordinador de Sistemas Escolares de UAM Iztapalapa

#### 3.2. Dominio de Desempeño de Alcance (*Scope Performance Domain*)

**Actividades clave:**\
- Elicitar requisitos mediante talleres con usuarios clave (coordinadores académicos, profesores, personal de servicios escolares).\
- Desarrollar estructura de desglose del trabajo (WBS) organizada por niveles tecnológicos con dependencias secuenciales explícitas.

> "En lugar de entregar todas las historias de usuario que se encuentran en el *backlog*, el equipo se enfoca en los objetivos principales del producto para satisfacer las expectativas del cliente. El alcance del proyecto se refina a través de diferentes iteraciones" (PMI, 2025, p. 45, traducción propia).

**Entregable práctico para el SiE:**\
- WBS organizada por niveles: Nivel 0 (Rocky Linux) → Nivel 1 (FreeIPA) → Nivel 2 (PostgreSQL) → Nivel 3 (Tomcat/Mayan EDMS) → Nivel 4 (iDempiere)\
- Matriz de trazabilidad que vincule configuraciones del Application Dictionary con requisitos de procesos académicos específicos de la UAM\
- Documentación UML de la arquitectura como activo intangible institucional para mitigar *organizational lock-in*

#### 3.3. Dominio de Desempeño de Cronograma (*Schedule Performance Domain*)

**Actividades clave:**\
- Definir actividades considerando las dependencias técnicas secuenciales (Nivel 0 debe completarse antes de iniciar Nivel 1).\
- Estimar esfuerzo utilizando *bottom-up estimating* considerando las 11 horas semanales por alumno en la fábrica de software educativa.\
- Desarrollar cronograma con enfoque predictivo para hitos de integración de niveles y adaptativo para configuración de workflows académicos.

> "Una técnica bien conocida que ayuda con este enfoque es la planificación por oleadas progresivas (*rolling wave planning*)" (PMI, 2025, p. 48, traducción propia).

**Entregable práctico para el SiE:**\
- Cronograma maestro de 8 semanas con hitos por nivel tecnológico\
- Buffer de proyecto (15% del tiempo total) para manejar curva de aprendizaje en tecnologías libres\
- Plan de integración progresiva validado: "FASE 1: FreeIPA (1-2 semanas) ↓ FASE 2: PostgreSQL 15 (1-2 semanas) ↓ FASE 3: Apache Tomcat 10 + Mayan EDMS 4.x (2-3 semanas) ↓ FASE 4: iDempiere 9.x (6-8 semanas)" (Zavala, 2026, p. 42)

#### 3.4. Dominio de Desempeño Financiero (*Finance Performance Domain*)

**Actividades clave:**\
- Estimar costos considerando únicamente recursos humanos (alumnos de la fábrica de software) y hardware virtualizado.\
- Desarrollar línea base de costos integrada con el cronograma, excluyendo licenciamientos comerciales gracias a la arquitectura 100% software libre.

> "La línea base de costos es la versión aprobada del presupuesto del proyecto distribuido en el tiempo, excluyendo cualquier reserva de gestión, la cual solo puede modificarse mediante procedimientos formales de control de cambios" (PMI, 2025, p. 126, traducción propia).

**Entregable práctico para el SiE:**\
- Estimación detallada por nivel tecnológico (ej. Nivel 0 Rocky Linux: 165 horas-hombre para instalación base, particionamiento LVM y configuración de seguridad)\
- Línea base de costos integrada con hitos de entrega semanales\
- Reservas de gestión (10% del esfuerzo total) para riesgos de configuración compleja

#### 3.5. Dominio de Desempeño de Partes Interesadas (*Stakeholders Performance Domain*)

**Actividades clave:**\
- Identificar partes interesadas institucionales: usuarios finales (alumnos, profesores), áreas administrativas (servicios escolares), equipos de TI institucional, autoridades académicas (coordinaciones).\
- Analizar expectativas mediante matriz de poder/interés considerando la resistencia potencial al cambio organizacional en procesos académicos tradicionales.

> "El engagement de partes interesadas es el proceso de comunicarse y trabajar con las partes interesadas para satisfacer sus necesidades/expectativas, abordar los problemas a medida que surgen y fomentar niveles apropiados de participación" (PMI, 2025, p. 70, traducción propia).

**Entregable práctico para el SiE:**\
- Registro de partes interesadas con clasificación específica para entorno universitario\
- Plan de engagement con demostraciones semanales de avances a coordinadores académicos\
- Canales de comunicación diferenciados (Slack para equipo técnico, sesiones presenciales para validación de workflows académicos)

#### 3.6. Dominio de Desempeño de Recursos (*Resources Performance Domain*)

**Actividades clave:**\
- Planificar recursos humanos considerando la estructura de la fábrica de software educativa (30 alumnos con roles especializados).\
- Definir estructura de equipo autónomo con capacidad para tomar decisiones técnicas dentro de las iteraciones semanales.\
- Planificar recursos físicos y virtuales (servidores virtuales sobre Rocky Linux 9.x con particionamiento LVM y cifrado LUKS2).

> "Los equipos de proyecto pueden estructurarse de diversas maneras dependiendo del enfoque del proyecto, su complejidad y el contexto organizacional. Los equipos adaptativos suelen presentar características de autoorganización" (PMI, 2025, p. 84, traducción propia).

**Entregable práctico para el SiE:**\
- Matriz de asignación de responsabilidades (RAM) con roles específicos para la fábrica de software educativa\
- Plan de formación acelerada (2 semanas iniciales) en tecnologías clave: Rocky Linux 9.x (SELinux, LUKS2, firewalld), FreeIPA, PostgreSQL 15, Application Dictionary de iDempiere - Especificaciones mínimas de hardware para PoC: "CPU: 4 vCPUs (x86_64), RAM: 16 GB, Almacenamiento: 100 GB SSD" (Zavala, 2026, p. 58)

#### 3.7. Dominio de Desempeño de Riesgos (*Risk Performance Domain*)

**Actividades clave:**\
- Identificar riesgos técnicos (complejidad inicial de configuración del Application Dictionary), organizacionales (curva de aprendizaje en software libre) y de proyecto (dependencia de conocimiento tácito).\
- Analizar probabilidad e impacto utilizando matriz cualitativa adaptada al contexto educativo.\
- Planificar respuestas: mitigación para riesgos técnicos mediante modelado UML previo; transferencia mediante documentación exhaustiva durante la PoC.

> "La categorización de riesgos. Las categorías de riesgo proporcionan un medio para agrupar riesgos individuales del proyecto. Una forma común de estructurar categorías de riesgo es mediante una estructura de desglose de riesgos (RBS)" (PMI, 2025, p. 97, traducción propia).

**Entregable práctico para el SiE:**\
- RBS con categorías específicas: técnicos (configuración ADD, hardening de Rocky Linux), organizacionales (resistencia al cambio), educativos (transferencia de conocimiento)\
- Registro de riesgos inicial priorizando "curva de aprendizaje en Application Dictionary" y "configuración inadecuada de Tomcat (seguridad, rendimiento)" como riesgos críticos\
- Plan de mitigación para Rocky Linux: "hardening progresivo (modo permissive en PoC → enforcing en producción); auditoría de puertos expuestos" (Zavala, 2026, p. 72)

### 4. Integración del Plan de Gestión del Proyecto para la PoC del SiE

El plan integrado incluye componentes específicos para el entorno académico:

> "El plan de gestión del proyecto es el documento que describe cómo se ejecutará, monitoreará, controlará y cerrará el proyecto. El plan de gestión del proyecto define la base para todas las decisiones del proyecto y es un documento vivo que puede esperarse que cambie con el tiempo" (PMI, 2025, p. 126, traducción propia).

Para el SiE, el plan integrado incluirá:\
- Componentes obligatorios adaptados: planes de alcance (enfocado en configuración sin código mediante ADD), cronograma (8 semanas con hitos por nivel tecnológico), recursos (estructura de fábrica de software educativa)\
- Anexos específicos: definición de "Done" para configuraciones del Application Dictionary, criterios de aceptación para workflows académicos, estrategia de documentación UML como activo intangible institucional\
- Mecanismos de control de cambios: comité técnico para decisiones arquitectónicas; equipo autónomo para configuraciones dentro del ADD

### 5. Consideraciones de *Tailoring* para la Fábrica de Software Educativa

El *tailoring* para el contexto educativo considera:

> "Las consideraciones y ejemplos de *tailoring* se insertan en cada dominio de desempeño. Estas consideraciones y ejemplos ilustran cómo los profesionales pueden aplicar conceptos de gestión de proyectos en contextos variados" (PMI, 2025, p. ix, traducción propia).

Para la PoC del SiE en una fábrica de software educativa:\
- **Enfoque de desarrollo:** Híbrido nivel 2 – predictivo para secuencia de integración de niveles tecnológicos (Nivel 0 → Nivel 4); adaptativo para configuración iterativa de procesos académicos mediante el Application Dictionary\
- **Métricas de progreso:** Velocidad del equipo (puntos de historia configurados/semana) para componentes adaptativos; cumplimiento de hitos técnicos para componentes predictivos\
- **Gobernanza educativa:** Reuniones de seguimiento semanales con el profesor actuando como Project Manager; ceremonias ágiles diarias para el equipo técnico de alumnos

------------------------------------------------------------------------

## Anexo 1: Plan del Proyecto de 8 Semanas para la Fábrica de Software

### Contexto Operativo

-   **Equipo:** 30 alumnos organizados como fábrica de software educativa
-   **Dedicación:** 11 horas semanales por alumno (330 horas-hombre/semana)
-   **Duración total:** 8 semanas (2,640 horas-hombre totales)
-   **Estructura de roles:**
    -   1 Project Manager (profesor supervisor)
    -   3 Arquitectos de solución (alumnos avanzados)
    -   12 Desarrolladores/Configuradores (especializados en componentes por nivel)
    -   6 QA/Testers (validación de workflows académicos)
    -   4 DevOps (gestión de infraestructura Rocky Linux y contenedores)
    -   4 Business Analysts (modelado de procesos académicos UAM)

### Cronograma Detallado

| Semana | Nivel Tecnológico | Actividades Clave | Entregables Validables | Horas-Hombre Asignadas |
|---------------|---------------|---------------|---------------|---------------|
| **1** | **Nivel 0: Rocky Linux 9.x** | \- Instalación mínima desde ISO DVD<br>- Configuración de particionamiento LVM con volúmenes separados (/boot, /, /var/lib/pgsql, /var/lib/mayan)<br>- Habilitación de cifrado LUKS2 para volumen de PostgreSQL<br>- Configuración inicial de firewalld con segmentación por zonas (interna vs. pública)<br>- Aplicación de actualizaciones de seguridad iniciales (`dnf update`) | \- Sistema base operativo con SELinux enforcing<br>- Particionamiento LVM validado con volúmenes lógicos separados<br>- Firewalld configurado con zonas segmentadas<br>- Reporte de parches de seguridad aplicados | 330 |
| **2** | **Nivel 1: FreeIPA** | \- Instalación y configuración básica del dominio `uamizt.mx`<br>- Definición de estructura organizacional LDAP (OU tree: ou=personas, ou=alumnos, ou=profesores)<br>- Configuración de políticas HBAC y SSSD para integración con Rocky Linux<br>- Creación de esquema de atributos personalizados UAM (matrícula, división académica) | \- Directorio LDAP funcional con 5 grupos institucionales<br>- Pruebas de autenticación SSO validadas desde Rocky Linux<br>- Documentación de políticas de acceso RBAC<br>- Schema LDIF con atributos UAM | 330 |
| **3** | **Nivel 2: PostgreSQL 15** | \- Instalación desde repositorio AppStream de Rocky Linux<br>- Configuración de particionamiento LVM para datos, WAL y respaldos<br>- Implementación del esquema relacional académico UAM<br>- Configuración de autenticación externa LDAP con FreeIPA<br>- Creación de índices estratégicos y vistas materializadas | \- Base de datos operativa con esquema UAM<br>- Scripts DDL completos y optimizados<br>- Pruebas de carga con 10,000 registros validadas<br>- Conexión LDAP funcional para autenticación de usuarios | 330 |
| **4** | **Nivel 3a: Apache Tomcat 10** | \- Instalación desde repositorio EPEL<br>- Configuración de memoria (`setenv.sh`: `-Xms4096m -Xmx4096m`)<br>- Configuración de pool de conexiones JDBC hacia PostgreSQL<br>- Hardening de seguridad progresivo (modo permissive SELinux)<br>- Integración con FreeIPA mediante mod_auth_gssapi | \- Contenedor Tomcat operativo con configuración de memoria optimizada<br>- DataSource JDBC funcional hacia PostgreSQL<br>- Pruebas de carga con 50 usuarios concurrentes validadas<br>- SSO funcional para aplicaciones Java | 330 |
| **5** | **Nivel 3b: Mayan EDMS 4.x** | \- Instalación y configuración inicial<br>- Definición de tipos documentales y metadatos (actas, trámites, credenciales)<br>- Configuración de workflows básicos con cumplimiento LGPD mexicana<br>- Integración con FreeIPA para autenticación LDAP<br>- Configuración de cifrado SSL/TLS con certificados institucionales | \- API REST funcional para gestión documental<br>- 5 tipos documentales configurados con metadatos estructurados<br>- Workflow de aprobación de actas operativo<br>- Mecanismos de cumplimiento LGPD implementados (cancelación, oposición, seguridad) | 330 |
| **6** | **Nivel 4a: iDempiere Base** | \- Instalación y configuración inicial del Application Dictionary<br>- Creación de tablas personalizadas mediante ADD (C_SIE_Alumno, M_SIE_UEA)<br>- Configuración de roles institucionales y organización UAM<br>- Integración con FreeIPA para autenticación SSO<br>- Integración con PostgreSQL como motor transaccional | \- Estructura base del ADD configurada<br>- Ventanas básicas operativas (alumnos, UEA, grupos)<br>- Mapeo LDAP-iDempiere funcional<br>- Esquema de base de datos extendido sin modificar núcleo | 330 |
| **7** | **Nivel 4b: Workflows Académicos I** | \- Configuración de workflow de inscripciones con validación de seriación<br>- Implementación de proceso "Generar Acta" con integración REST a Mayan EDMS<br>- Configuración de portal de alumnos con ZK<br>- Pruebas end-to-end de casos críticos (inscripción, generación de acta) | \- Workflow de inscripciones validado con reglas de seriación<br>- Proceso de generación automática de actas funcional<br>- Integración bidireccional iDempiere-Mayan operativa<br>- Portal web funcional para consulta de calificaciones | 330 |
| **8** | **Integración y Cierre** | \- Pruebas end-to-end de casos de uso críticos (admisión a titulación)<br>- Documentación técnica exhaustiva (diagramas UML, runbooks, manuales)<br>- Demostración final a stakeholders institucionales<br>- Elaboración de acta de cierre con lecciones aprendidas | \- Reporte de pruebas con 100% de casos críticos aprobados<br>- Manual de administración y troubleshooting<br>- Diagramas UML de arquitectura como activo intangible<br>- Acta de cierre de PoC con lecciones aprendidas | 330 |

### Métricas de Éxito para la PoC

La PoC se considerará exitosa cuando se cumplan los siguientes criterios técnicos institucionales:\
1. **Integración funcional:** Los seis componentes operan en secuencia sin puntos únicos de falla (Nivel 0 → Nivel 4)\
2. **Configuración sin código:** Todos los procesos académicos modelados mediante Application Dictionary sin desarrollo Java personalizado\
3. **Cumplimiento normativo:** Gestión documental con trazabilidad completa conforme a LGPD mexicana; cifrado LUKS2 para datos sensibles en Rocky Linux\
4. **Transferencia de conocimiento:** Documentación técnica UML suficiente para operación autónoma por parte del personal institucional\
5. **Soberanía tecnológica validada:** Arquitectura 100% software libre sin dependencia de licenciamientos comerciales ni vendor lock-in

### Consideraciones Pedagógicas

-   Cada semana incluye 2 horas de ceremonias ágiles (planificación, retrospectiva) y 9 horas de trabajo técnico
-   Los roles rotan parcialmente cada 2 semanas para maximizar la formación en múltiples dominios técnicos (Niveles 0-4)
-   Se documenta exhaustivamente cada configuración mediante diagramas UML como activo intangible institucional, alineado con el principio de capitalización de conocimiento tácito identificado en el estudio de factibilidad (Zavala, 2026)
-   El profesor actúa como Project Manager facilitador, promoviendo la autonomía del equipo según el principio *"Construir una Cultura Empoderada"* (PMI, 2025, p. 53, traducción propia)

------------------------------------------------------------------------

**Referencias**

Project Management Institute. (2025). *A guide to the project management body of knowledge (PMBOK® guide)* (8th ed.). Project Management Institute.

Smyth, N. (2023). *Rocky Linux 9 essentials*. Payload Media, Inc.

Zavala, J. (2026). *Reporte Técnico 02: Estudio de factibilidad de la Prueba de Concepto del SiE* [Documento interno de clase]. Universidad Autónoma Metropolitana Unidad Iztapalapa.
