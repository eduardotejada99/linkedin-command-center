# 📘 Data & AI de Cero a Cien
### De SQL y BI a Agentes Autónomos, Semantic Layers y MCP
**Autor del roadmap:** Eduardo Tejada Reyes | CIP 372629  
**Actualizado:** Octubre 2026  
**Repositorio:** [github.com/eduardotejada99/linkedin-command-center](https://github.com/eduardotejada99/linkedin-command-center)

---

> Esta guía tiene doble propósito: es tu plan personal de upskilling técnico y es el calendario maestro de contenido que publicarás en LinkedIn. Cada capítulo que estudias y aplicas en producción se convierte en un post de autoridad, un módulo de código en GitHub o una herramienta que demuestra tu dominio ante cualquier reclutador o CTO.

---

## 📌 Índice General

| Nivel | Capítulos | Foco |
| :--- | :--- | :--- |
| 🟢 **Nivel 1: Fundamentos** | 1 al 4 | Ciclo del dato, SQL avanzado, modelado dimensional, auditoría de calidad |
| 🟡 **Nivel 2: Analytics Engineering** | 5 al 9 | dbt Core, arquitectura en capas, linaje, Power BI empresarial |
| 🟠 **Nivel 3: AI-Native & Agentes** | 10 al 15 | Herramientas agénticas, MCP, servidores Python, orquestación |
| 🔴 **Nivel 4: Producción & IA Empresarial** | 16 al 20 | Semantic Layer, Text-to-SQL, Evals, ML de negocio, despliegue |
| 🟣 **Nivel 5: AI Engineering de Élite** | 21 al 25 | RAG avanzado, Vector DBs, Fine-Tuning, LangGraph multi-agente, LLMOps |

---

## 🟢 NIVEL 1: Fundamentos del Dato en Producción

> El dato limpio es la base de todo. Sin esta capa bien construida, los modelos de Machine Learning mienten y los agentes de IA alucinan.

---

### Capítulo 1: El Ciclo del Dato en Producción

**Qué aprenderás:**
- Diferencia entre OLTP (datos transaccionales) y OLAP (datos analíticos): por qué mezclarlos es un error crítico.
- Flujo completo del dato: Ingesta bruta → Staging → Transformación → Tablero o Modelo de IA.
- El principal error de las empresas: conectar una herramienta de visualización directamente a la base transaccional de producción.

**Recursos recomendados:**
- Documentación oficial de dbt sobre capas de arquitectura.
- Artículo: *"The Data Engineering Lifecycle"* (Fundamentals of Data Engineering, Reis & Housley).

**Proyecto práctico:**
- Dibuja en papel y digitaliza el diagrama del flujo de datos actual de tu trabajo en RIS Cajabamba: qué tabla vive dónde, qué sistema la produce y qué herramienta la consume hoy.

**Post de LinkedIn sugerido:**
> *"El 80% de los errores en reportes de salud que he visto no vienen del modelo de BI. Vienen de conectar Power BI directo a las tablas transaccionales del HIS sin una capa intermedia. Aquí explico por qué eso rompe todo."*

---

### Capítulo 2: SQL Avanzado de Verdad

**Qué aprenderás:**
- Window Functions: `ROW_NUMBER()`, `RANK()`, `DENSE_RANK()`, `LEAD()`, `LAG()` y marcos de partición (`ROWS BETWEEN`).
- CTEs recursivas: para jerarquías organizacionales, rutas de red y estructuras de árbol de establecimientos de salud.
- Planes de ejecución (`SET STATISTICS IO ON` en SQL Server, `EXPLAIN ANALYZE` en Postgres): identificar Table Scans, operadores de hash y cuellos de botella.
- Índices clustered vs non-clustered, índices cubrientes y estrategia de particionamiento horizontal.
- Diferencias de comportamiento en SQL Server vs PostgreSQL (para que puedas trabajar en ambos motores sin sorpresas).

**Recursos recomendados:**
- *Use The Index, Luke* (use-the-index-luke.com) — La mejor guía gratuita de indexación y planes de ejecución.
- Documentación oficial de `sys.dm_exec_query_plan` en SQL Server.
- *SQL Antipatterns* (Bill Karwin) — Capítulos 4, 9 y 14.

**Proyecto práctico:**
- Toma una consulta lenta de tu trabajo actual (o crea una sobre un dataset público de salud en Kaggle). Analiza su plan de ejecución, identifica el operador más costoso, agrega el índice correcto y compara los tiempos antes y después con capturas de pantalla.

**Post de LinkedIn sugerido:**
> *"Esta consulta tardaba 40 segundos. Ahora tarda 0.3. Un índice cubriente y reescribir la subcorrelacionada. Aquí muestro el plan de ejecución antes y después."*

---

### Capítulo 3: Modelado Dimensional Moderno

**Qué aprenderás:**
- Kimball vs Inmon: diferencias prácticas y cuándo usar cada enfoque.
- Tablas de Hechos (Fact tables): tipos transaccionales, de snapshot periódico y acumulativos.
- Tablas de Dimensiones (Dimension tables): SCD Tipo 1, Tipo 2 y Tipo 3 en la práctica.
- El patrón moderno One Big Table (OBT) y cuándo es preferible al esquema estrella clásico en Data Warehouses en la nube (BigQuery, Snowflake, DuckDB).
- Claves surrogate vs claves de negocio: por qué importa la distinción.

**Recursos recomendados:**
- *The Data Warehouse Toolkit* (Kimball, Ross) — Capítulos 1, 2 y 3.
- Guía de dbt sobre mejores prácticas de modelado (docs.getdbt.com/guides/best-practices).
- Artículo: *"Medallion Architecture: Bronze, Silver, Gold"* (Databricks Docs).

**Proyecto práctico:**
- Diseña el modelo dimensional de tus datos de RIS Cajabamba: una Fact Table de atenciones médicas con sus dimensiones de Establecimiento, Tiempo, Diagnóstico (CIE-10) y Paciente. Diagrama en dbdiagram.io o Draw.io.

**Post de LinkedIn sugerido:**
> *"Mucha gente construye dashboards de salud sobre tablas planas sin modelar. Aquí comparto el esquema de estrella que usé para consolidar atenciones de 15 centros de salud en una sola tabla de hechos."*

---

### Capítulo 4: Auditoría y Calidad de Datos

**Qué aprenderás:**
- Dimensiones de calidad de datos: Completitud, Unicidad, Consistencia, Validez y Puntualidad.
- Consultas de auditoría automatizadas: detección de duplicados silenciosos, nulos inesperados y rangos inválidos.
- Reconciliación de totales: cómo verificar que el número que ves en Power BI coincide con la fuente transaccional.
- Documentación de reglas de negocio como código.

**Recursos recomendados:**
- Documentación de dbt tests: `unique`, `not_null`, `accepted_values`, `relationships`.
- Framework *Great Expectations* (greatexpectations.io) para validaciones en Python.

**Proyecto práctico:**
- Escribe 10 consultas de auditoría en SQL contra un dataset de salud pública (MINSA Perú publica datasets en datosabiertos.gob.pe). Detecta al menos 3 anomalías reales y documenta el hallazgo con su impacto potencial.

**Post de LinkedIn sugerido:**
> *"Antes de construir cualquier dashboard, corro 10 consultas de auditoría sobre la base. Aquí están las que nunca me fallan para detectar datos corruptos en sistemas de salud."*

---

## 🟡 NIVEL 2: Analytics Engineering & Modern Data Stack

> Este nivel te convierte de "analista que hace dashboards" en "analytics engineer que construye la arquitectura de datos confiable que alimenta dashboards y modelos de IA".

---

### Capítulo 5: Introducción a dbt Core

**Qué aprenderás:**
- Qué es dbt y por qué se convirtió en el estándar de transformación de datos en empresas modernas.
- Arquitectura de un proyecto dbt: `models/`, `tests/`, `macros/`, `seeds/`, `snapshots/`.
- Instalación local de dbt con Postgres (DuckDB como alternativa rápida sin servidor).
- El flujo de trabajo básico: `dbt run`, `dbt test`, `dbt docs generate`.
- Materializations: `view`, `table`, `incremental`, `ephemeral`.

**Recursos recomendados:**
- Curso oficial gratuito *dbt Fundamentals* (courses.getdbt.com).
- Documentación: docs.getdbt.com.
- Repositorio oficial de ejemplo: jaffle_shop (el proyecto de práctica estándar de la comunidad dbt).

**Proyecto práctico:**
- Configura un proyecto dbt local con DuckDB o Postgres. Replica el jaffle_shop completo. Ejecuta `dbt run`, `dbt test` y genera la documentación con el linaje visual.

**Post de LinkedIn sugerido:**
> *"dbt vs. un procedimiento almacenado: por qué un equipo de datos en 2026 elige dbt para transformaciones. Aquí la comparación práctica con el mismo problema resuelto de ambas formas."*

---

### Capítulo 6: Arquitectura en Capas: Staging, Intermediate y Marts

**Qué aprenderás:**
- La arquitectura de tres capas de dbt y por qué esta separación es crítica.
- **Staging:** Una fuente de datos, un modelo. Sin lógica de negocio. Solo renombrado, casteos de tipos y estandarización.
- **Intermediate:** Lógica de negocio compleja, joins entre fuentes, enriquecimiento de datos.
- **Marts:** Entidades de negocio limpias y listas para consumir desde BI o desde modelos de IA.
- Convenciones de nomenclatura estándar (`stg_`, `int_`, `fct_`, `dim_`).

**Recursos recomendados:**
- Guía oficial de dbt: *"How we structure our dbt projects"*.
- Blog de dbt Labs: *"The layered data architecture explained"*.

**Proyecto práctico:**
- Diseña y construye en dbt las tres capas para los datos de atenciones médicas (usando el modelo dimensional diseñado en el Cap. 3). Crea al menos 2 modelos por capa con sus relaciones documentadas.

**Post de LinkedIn sugerido:**
> *"Por qué en mis proyectos de datos en salud nunca toco la base transaccional desde Power BI. La arquitectura en capas de dbt que usamos para separar la ingesta, la transformación y el análisis."*

---

### Capítulo 7: Testing Automatizado de Datos con dbt

**Qué aprenderás:**
- Tests genéricos de dbt: `unique`, `not_null`, `accepted_values`, `relationships`.
- Tests singulares: SQL personalizado para validar reglas de negocio complejas.
- Packages de testing avanzado: `dbt-utils` y `dbt-expectations` (extensiones del Great Expectations dentro de dbt).
- Estrategia de testing: qué columnas testear, con qué frecuencia y qué hacer cuando un test falla en producción.
- Integración de tests en pipelines de CI/CD con GitHub Actions.

**Recursos recomendados:**
- Documentación oficial de dbt tests.
- Paquete `dbt-expectations` en hub.getdbt.com.

**Proyecto práctico:**
- Agrega al menos 15 tests a tu proyecto de dbt del Cap. 6. Incluye: tests genéricos en todas las columnas clave, un test singular de reconciliación de totales y un test de rango válido de fechas.

**Post de LinkedIn sugerido:**
> *"Un analista me dijo: 'Si los datos están mal, me lo dice el jefe cuando el reporte falla'. Aquí muestro cómo configuré 15 tests automáticos que detectan problemas antes de que el pipeline llegue a Power BI."*

---

### Capítulo 8: Linaje de Datos y Documentación Automática

**Qué aprenderás:**
- Qué es el linaje de datos (data lineage) y por qué es el primer requisito de cualquier equipo de datos maduro.
- Generación del DAG (Directed Acyclic Graph) de dependencias con `dbt docs generate`.
- Documentación de modelos con bloques `description` en archivos `.yml` y uso de `doc()`.
- Descubrimiento de datos: cómo un equipo de analistas puede entender la arquitectura sin pedir explicaciones.
- Herramientas complementarias de catálogo de datos: OpenMetadata y DataHub (overview).

**Recursos recomendados:**
- Documentación de dbt sobre `dbt docs`.
- Artículo: *"Data Observability Explained"* (Monte Carlo Data Blog).

**Proyecto práctico:**
- Documenta todos los modelos de tu proyecto dbt. Genera la web local de documentación y captura el DAG de dependencias. Escribe descripciones detalladas de las 5 columnas más importantes de tu fact table.

**Post de LinkedIn sugerido:**
> *"Heredé un proyecto de SQL Server con 200 procedimientos almacenados sin documentar. Aquí cómo recreé el linaje de datos en dbt y generé documentación automática en 2 días."*

---

### Capítulo 9: Power BI Empresarial con DAX Avanzado

**Qué aprenderás:**
- Contexto de fila vs contexto de filtro: la base de todo en DAX.
- Funciones de inteligencia temporal: `DATEADD()`, `SAMEPERIODLASTYEAR()`, `TOTALYTD()`, rolling averages.
- Optimización con DAX Studio y VertiPaq Analyzer: identificar medidas lentas y columnas sobredimensionadas.
- Modelo tabular limpio: por qué no debes traer columnas innecesarias desde SQL a Power BI.
- Diseño de medidas con el patrón CALCULATE + FILTER para cálculos de cohortes complejos.

**Recursos recomendados:**
- *The Definitive Guide to DAX* (Ferrari, Russo).
- DAX Studio (daxstudio.org) — Gratuito.
- SQLBI.com — El mejor recurso gratuito de DAX del mundo.

**Proyecto práctico:**
- Construye un modelo tabular en Power BI conectado a los marts de dbt (Cap. 6). Escribe 5 medidas DAX avanzadas: total atenciones, variación MoM, YTD, promedio móvil de 12 semanas y ratio de cobertura vs meta. Audita el performance con DAX Studio.

**Post de LinkedIn sugerido:**
> *"3 errores de DAX que hacen que tu modelo de Power BI sea un 10x más lento de lo necesario. Los veo en casi todos los proyectos que hereda mi equipo."*

---

## 🟠 NIVEL 3: AI-Native & Flujos Agénticos

> Este nivel transforma cómo trabajas día a día. En lugar de usar la IA como un buscador sofisticado, la integras en tu flujo de ingeniería para multiplicar tu capacidad de producción.

---

### Capítulo 10: El Entorno AI-Native para Ingenieros de Datos

**Qué aprenderás:**
- Diferencia entre usar IA como herramienta de chat vs. como motor de tu flujo de trabajo de ingeniería.
- Configuración de un entorno AI-Native: Antigravity IDE (o Claude Code) + editor de código + terminal.
- El archivo de contexto de proyecto (`CLAUDE.md` / `AGENTS.md`): cómo darle a un agente todo el contexto de tu arquitectura de datos sin repetirlo en cada sesión.
- Técnicas de prompting para ingenieros de datos: cómo pedir refactorización de queries complejas, generación de modelos dbt y análisis de planes de ejecución.

**Recursos recomendados:**
- Documentación de Anthropic sobre Claude Code y MCP.
- El repositorio que tienes en mano: github.com/eduardotejada99/linkedin-command-center.

**Proyecto práctico:**
- Configura un archivo `CLAUDE.md` en tu proyecto dbt de Cajabamba que documente: el motor de base de datos (SQL Server), las convenciones de nomenclatura, la arquitectura de capas y los tests mínimos requeridos por tabla. Usa el agente para generar un modelo de staging automáticamente y evalúa la calidad del resultado.

**Post de LinkedIn sugerido:**
> *"Cómo configuré mi proyecto de dbt para que un agente de IA entienda el contexto de mi arquitectura de salud desde el primer mensaje. El archivo que cambió mi productividad."*

---

### Capítulo 11: Contexto y Memoria en Proyectos de Datos Largos

**Qué aprenderás:**
- Cómo funciona la ventana de contexto de los modelos y por qué se pierden detalles en conversaciones largas.
- Técnicas de compresión de contexto: documentos de referencia, `CLAUDE.md`, archivos de `voice.md` y `about-me.md` en tu proyecto.
- Memoria externa persistente con Knowledge Graph MCP (grafo de entidades y relaciones de tu arquitectura de datos).
- Manejo de proyectos de datos complejos en sesiones de IA largas sin perder el hilo.

**Recursos recomendados:**
- Documentación de Anthropic sobre manejo de contexto largo.
- MCP Memory Server (servidor oficial de memoria en grafo).

**Proyecto práctico:**
- Construye el grafo de entidades de tu arquitectura de datos en el MCP de memoria: tablas, relaciones entre fuentes, dueños de cada capa, reglas de calidad críticas. Prueba que el agente puede responder preguntas sobre tu arquitectura sin que se las expliques desde cero.

**Post de LinkedIn sugerido:**
> *"El mayor problema de usar IA en proyectos de datos reales: pierde el contexto de tu arquitectura a mitad de sesión. Cómo lo resolví con un grafo de memoria persistente."*

---

### Capítulo 12: Model Context Protocol (MCP): La Revolución de la Conexión

**Qué aprenderás:**
- Qué es MCP (Model Context Protocol) y por qué se está convirtiendo en el protocolo estándar para conectar LLMs a herramientas empresariales.
- Arquitectura de MCP: cliente, servidor, recursos, herramientas y prompts.
- Servidores MCP oficiales disponibles: File System, GitHub, Postgres, SQL Server, Google Drive y más.
- Configuración de servidores MCP existentes en tu entorno de trabajo (exactamente como ya tienes configurado en tu Antigravity IDE).
- Diferencia entre RAG tradicional y MCP: cuándo usar cada arquitectura.

**Recursos recomendados:**
- Especificación oficial: modelcontextprotocol.io.
- Repositorio: github.com/modelcontextprotocol/servers.
- Artículo: *"MCP: A new standard for connecting AI models to data"* (Anthropic Blog).

**Proyecto práctico:**
- Configura el servidor MCP oficial de Postgres en tu entorno local. Conéctalo a tu base de datos del proyecto dbt. Verifica que el agente puede leer el schema de tus tablas y responder preguntas sobre tus datos sin que escribas SQL manualmente.

**Post de LinkedIn sugerido:**
> *"MCP vs. RAG: cuál usar para conectar un asistente de IA a bases de datos SQL empresariales. La diferencia práctica que nadie explica bien en español."*

---

### Capítulo 13: Construyendo tu Primer Servidor MCP en Python

**Qué aprenderás:**
- SDK oficial de MCP en Python (`mcp` package de Anthropic).
- Estructura de un servidor MCP mínimo: `@server.list_tools()` y `@server.call_tool()`.
- Exposición segura de consultas SQL predefinidas: cómo permitir que un agente consulte tus datos sin aceptar SQL arbitrario del usuario (prevención de inyección SQL).
- Implementación de un servidor MCP que expone métricas específicas de tu dominio (ej: cobertura de vacunas, tiempos de parada de maquinaria) como herramientas tipadas.
- Logging, manejo de errores y testing de servidores MCP.

**Recursos recomendados:**
- Repositorio oficial de ejemplos: github.com/modelcontextprotocol/python-sdk.
- Guía de construcción de servidores MCP: modelcontextprotocol.io/quickstart/server.

**Proyecto práctico:**
- Construye un servidor MCP en Python con 3 herramientas:
  1. `get_coverage_summary(establecimientos, periodo)`: cobertura de vacunación por establecimiento.
  2. `get_top_diagnoses(periodo, n)`: los N diagnósticos más frecuentes.
  3. `list_data_quality_alerts()`: alertas de calidad de datos pendientes.

**Post de LinkedIn sugerido:**
> *"Construí un servidor MCP en 80 líneas de Python que expone métricas de salud sanitaria a cualquier asistente de IA. Aquí el código y el resultado."*

---

### Capítulo 14: Skills y Automatizaciones Personalizadas

**Qué aprenderás:**
- El sistema de Skills de Antigravity: cómo crear instrucciones especializadas para flujos de trabajo repetitivos.
- Construcción de una skill de data engineering: generación automática de modelos dbt y tests a partir de una descripción del dataset.
- Hooks de automatización: disparadores automáticos al crear o modificar archivos en tu proyecto.
- Orquestación de tareas de datos complejas en paralelo con subagentes.

**Recursos recomendados:**
- Documentación de Antigravity sobre el sistema de Skills y SKILL.md.
- Tu repositorio de skills: C:\Users\ETEJADA\.gemini\config\skills\.

**Proyecto práctico:**
- Crea una skill personalizada llamada `dbt-model-generator` que, dado el nombre de una tabla fuente y una lista de columnas, genere automáticamente: el modelo de staging, el archivo `.yml` con descripciones, y 5 tests mínimos de integridad.

**Post de LinkedIn sugerido:**
> *"Creé una skill que genera modelos dbt completos (SQL + YAML + tests) a partir de una descripción de tabla. De 2 horas a 3 minutos de configuración. Aquí cómo lo construí."*

---

### Capítulo 15: Orquestación Agéntica y Subagentes Especializados

**Qué aprenderás:**
- Arquitecturas multi-agente: agente orquestador que delega tareas a subagentes especializados.
- Patrones de trabajo paralelo: cuándo dividir una tarea grande en agentes independientes vs. cuándo mantenerla secuencial.
- Coordinación de agentes de datos: agente de calidad, agente de transformación, agente de documentación y agente de test.
- Manejo de errores y recuperación en flujos agénticos largos.

**Recursos recomendados:**
- Blog de Anthropic: *"Building effective agents"*.
- Skill de Antigravity: `dispatching-parallel-agents`.

**Proyecto práctico:**
- Diseña una arquitectura de 3 subagentes que trabajen en paralelo para un pipeline de migración de datos:
  1. Agente A: Analiza la fuente y genera el modelo de staging dbt.
  2. Agente B: Genera los tests de integridad.
  3. Agente C: Escribe la documentación de los modelos.

**Post de LinkedIn sugerido:**
> *"Migré un pipeline de ETL de 5 horas a un sistema de 3 agentes especializados trabajando en paralelo. Aquí el diagrama y los resultados."*

---

## 🔴 NIVEL 4: Sistemas de IA en Producción

> El nivel que separa al profesional de datos que usa IA del ingeniero que construye infraestructura de IA empresarial confiable.

---

### Capítulo 16: La Capa Semántica para LLMs (Semantic Layer & dbt MetricFlow)

**Qué aprenderás:**
- Por qué conectar un LLM directamente a una base de datos produce alucinaciones métricas sistemáticas.
- Capa Semántica (Semantic Layer): definición centralizada de métricas de negocio como código versionado.
- dbt MetricFlow: definición de métricas con dimensiones, filtros y granularidades desde dbt.
- Herramientas complementarias: Cube.js y LookML (Looker) para organizaciones más grandes.
- Cómo el LLM consume métricas predefinidas en lugar de inventar SQL sobre tablas crudas.

**Recursos recomendados:**
- Documentación de dbt MetricFlow: docs.getdbt.com/docs/build/metrics-overview.
- Artículo: *"The Semantic Layer: The Missing Piece in the Modern Data Stack"*.

**Proyecto práctico:**
- Define 5 métricas de negocio en dbt MetricFlow para tu proyecto de salud: `total_atenciones`, `cobertura_vacunacion`, `promedio_espera_atencion`, `ratio_citas_vs_meta`, `establecimientos_activos`. Verifica que el agente puede responder preguntas sobre estas métricas sin generar SQL incorrecto.

**Post de LinkedIn sugerido:**
> *"Conecté ChatGPT directamente a nuestra base de datos de salud y las métricas estaban mal. Aquí cómo la Capa Semántica con dbt MetricFlow resolvió las alucinaciones del modelo."*

---

### Capítulo 17: Text-to-SQL Empresarial Seguro

**Qué aprenderás:**
- Arquitectura de un sistema Text-to-SQL de producción: el flujo completo desde la pregunta del usuario hasta la respuesta validada.
- Prevención de inyección SQL: por qué los sistemas Text-to-SQL ingenuos son una vulnerabilidad de seguridad crítica.
- Patrones de validación de queries generadas por IA antes de ejecutarlas en producción.
- Construcción de un asistente analítico en Streamlit o FastAPI conectado a tu base de datos vía MCP.
- Manejo de preguntas ambiguas: cómo el sistema debe pedir aclaración en lugar de asumir.

**Recursos recomendados:**
- Paper: *"Spider: A Large-Scale Human-Labeled Dataset for Complex and Cross-Domain Semantic Parsing and Text-to-SQL Task"*.
- Biblioteca: Vanna.AI (text-to-SQL sobre bases de datos relacionales).
- Biblioteca: SQLAlchemy para ejecución segura de consultas parametrizadas.

**Proyecto práctico:**
- Construye un prototipo de asistente Text-to-SQL en Streamlit para consultar tu proyecto dbt. Implementa: whitelist de tablas permitidas, sanitización de la query generada, validación del schema antes de ejecutar y log de todas las consultas realizadas.

**Post de LinkedIn sugerido:**
> *"Construí un asistente que responde preguntas sobre datos de salud en lenguaje natural. Aquí los 5 problemas de seguridad que tuve que resolver antes de dejarlo en producción."*

---

### Capítulo 18: LLM Evals con Ragas y DeepEval

**Qué aprenderás:**
- Por qué la demostración de un sistema de IA no es suficiente: la necesidad de evaluación matemática rigurosa.
- Métricas fundamentales de evaluación de sistemas RAG y Text-to-SQL:
  - *Faithfulness*: ¿La respuesta está respaldada por los datos recuperados?
  - *Answer Relevance*: ¿El sistema respondió lo que el usuario preguntó?
  - *Context Precision*: ¿La consulta SQL generada trajo solo lo necesario?
  - *Context Recall*: ¿Se recuperaron todos los datos relevantes para responder?
- Framework Ragas: instalación, configuración y generación de datasets de evaluación sintéticos.
- Integración de Evals en CI/CD: rechazar automáticamente un cambio en el pipeline si el score de evaluación baja.

**Recursos recomendados:**
- Documentación de Ragas: docs.ragas.io.
- Documentación de DeepEval: docs.confident-ai.com.
- Paper: *"RAGAS: Automated Evaluation of Retrieval Augmented Generation"*.

**Proyecto práctico:**
- Crea un conjunto de 20 preguntas de evaluación sobre tus datos de salud con sus respuestas esperadas. Ejecuta Ragas sobre el sistema Text-to-SQL del Cap. 17. Reporta los scores de las 4 métricas y propón una mejora concreta para el score más bajo.

**Post de LinkedIn sugerido:**
> *"Mi asistente de analítica sanitaria tenía un 73% de faithfulness. Aquí qué significaba eso en la práctica y qué cambié para llevarlo al 91%."*

---

### Capítulo 19: Machine Learning Clásico para Negocio

**Qué aprenderás:**
- Los 3 problemas universales de negocio que ML resuelve mejor que un dashboard: Churn/abandono, Forecasting/demanda y Segmentación.
- Ciclo completo de un proyecto de ML de negocio: problema → datos → features → modelo → evaluación → despliegue.
- XGBoost y LightGBM: los modelos más usados en producción por su interpretabilidad y rendimiento.
- Series de tiempo para forecasting: Prophet y ARIMA para predecir demanda hospitalaria, consumo de insumos o fallos de maquinaria.
- Métricas de evaluación orientadas a negocio: ROC-AUC, F1 por clase, costo de falsos negativos vs positivos, Lift Charts.
- SHAP Values: cómo explicar el modelo a un director sin que sepa nada de estadística.

**Recursos recomendados:**
- *Hands-On Machine Learning with Scikit-Learn, Keras & TensorFlow* (Géron) — Capítulos 3, 6, 7 y 8.
- Documentación de XGBoost y Prophet.
- Kaggle: Datasets de salud y telemetría industrial para práctica.

**Proyecto práctico:**
- Construye un modelo de predicción de incumplimiento de citas médicas (no-show) usando un dataset público de salud. Evalúa con ROC-AUC y Precision-Recall. Genera un gráfico SHAP de las 5 variables más importantes. Documenta el análisis de costo del error (cuánto cuesta un falso negativo en el sistema de salud).

**Post de LinkedIn sugerido:**
> *"Construí un modelo para predecir qué pacientes no asistirán a su cita médica. ROC-AUC de 0.84. Aquí el análisis de SHAP y por qué la variable más predictiva fue inesperada."*

---

### Capítulo 20: Despliegue, APIs y Observabilidad en la Nube

**Qué aprenderás:**
- FastAPI para construir APIs de inferencia de modelos de ML: endpoints de predicción, documentación automática y manejo de versiones de modelos.
- Dockerización de servicios de datos: contenedores reproducibles para dbt, servidores MCP y APIs de inferencia.
- Despliegue en Microsoft Azure (aprovechando tu experiencia previa): Azure Container Apps, Azure Functions y Azure ML.
- Observabilidad de sistemas de IA: Langfuse y Arize Phoenix para monitorear agentes de lenguaje natural y detectar degradación de modelos en producción.
- GitHub Actions para CI/CD: pipeline automático que ejecuta `dbt test` + Evals de Ragas antes de cada despliegue.

**Recursos recomendados:**
- Documentación de FastAPI: fastapi.tiangolo.com.
- Documentación de Docker y Azure Container Apps.
- Langfuse: langfuse.com (open source, auto-hosteable).

**Proyecto práctico:**
- Empaqueta el asistente Text-to-SQL del Cap. 17 en un contenedor Docker. Despliégalo en Azure Container Apps. Conecta Langfuse para registrar cada consulta del sistema en producción. Configura una alerta si el score de faithfulness baja del 85%.

**Post de LinkedIn sugerido:**
> *"El asistente de datos que construí en el Cap. 17 ya está en producción en Azure. Aquí el pipeline completo: Docker + CI/CD con dbt tests + observabilidad con Langfuse."*

---

## 📊 Resumen del Mapa de Contenido LinkedIn (20 Posts de Autoridad)

| Cap | Gancho del Post | Pilar |
| :--- | :--- | :--- |
| 1 | El error más costoso en BI de salud: conectar Power BI directo a producción | Arquitectura del Dato |
| 2 | Query que tardaba 40 seg ahora tarda 0.3 seg — plan de ejecución antes/después | SQL Avanzado |
| 3 | Cómo modelé atenciones de 15 centros de salud en un esquema de estrella | Modelado Dimensional |
| 4 | Las 10 consultas de auditoría que corro antes de tocar cualquier base de datos | Calidad de Datos |
| 5 | dbt vs. stored procedures: la comparación práctica que le muestro a todo equipo | dbt Core |
| 6 | La arquitectura en capas que separa tu lógica de negocio de tus datos crudos | Staging / Marts |
| 7 | 15 tests automáticos que detectan datos corruptos antes de que rompan Power BI | Testing con dbt |
| 8 | Heredé 200 stored procedures sin documentar. Así reconstruí el linaje en 2 días | Linaje de Datos |
| 9 | 3 errores de DAX que hacen tu modelo 10x más lento | Power BI Avanzado |
| 10 | El archivo que le explica al agente de IA toda mi arquitectura desde el primer mensaje | AI-Native Workflow |
| 11 | Por qué los agentes de IA pierden el hilo en proyectos de datos largos y cómo lo resuelvo | Memoria en IA |
| 12 | MCP vs. RAG: cuál usar para conectar IA a bases de datos SQL | MCP |
| 13 | Construí un servidor MCP en 80 líneas que expone métricas de salud a cualquier asistente | MCP en Python |
| 14 | De 2 horas a 3 minutos: la skill que genera modelos dbt automáticamente | Skills Agénticas |
| 15 | 3 agentes trabajando en paralelo para migrar un pipeline ETL completo | Orquestación |
| 16 | Cómo la Capa Semántica de dbt eliminó las alucinaciones métricas de nuestro asistente | Semantic Layer |
| 17 | 5 problemas de seguridad que resolví antes de poner Text-to-SQL en producción | Text-to-SQL |
| 18 | Mi asistente tenía 73% de faithfulness. Qué hice para llegar al 91% | LLM Evals |
| 19 | Modelo que predice no-show de pacientes — ROC-AUC 0.84 y el hallazgo inesperado | ML de Negocio |
| 20 | El pipeline completo en producción: Docker + dbt CI/CD + observabilidad con Langfuse | DevOps de Datos |

---

## 🟣 NIVEL 5: AI Engineering de Élite (Lo que Contratan Google, Meta, Anthropic y OpenAI)

> Aquí la diferencia entre un profesional que *usa* IA y uno que *construye infraestructura de IA empresarial*. Este nivel replica exactamente lo que los mejores equipos de IA del mundo exigen en sus entrevistas técnicas.

---

### Capítulo 21: RAG Avanzado — Más Allá del Chatbot Básico

**Qué aprenderás:**
- Por qué el RAG básico (chunk → embed → search → LLM) falla en producción: ruido semántico, contexto perdido y respuestas incoherentes.
- **Chunking semántico**: fragmentar por estructura del documento (jerarquía Markdown, secciones de PDF) en lugar de por número fijo de tokens.
- **Parent-child chunking**: indexar chunks pequeños para búsqueda de precisión y recuperar el documento padre para contexto completo.
- **Hybrid search**: combinar búsqueda densa (embeddings de similitud semántica) con búsqueda dispersa (BM25/keyword) para capturar tanto la intención como términos exactos (códigos CIE-10, IDs de equipos, nombres de establecimientos).
- **Reranking con cross-encoders**: filtrar los top-N resultados del vector store con un modelo de reranking (Cohere Rerank, BGE-Reranker) antes de pasarlos al LLM.
- **HyDE (Hypothetical Document Embeddings)** y query decomposition: técnicas de transformación de consultas para mejorar el recall en preguntas ambiguas.

**Recursos recomendados:**
- Documentación de LlamaIndex sobre advanced RAG pipelines.
- Paper: *RAGAS: Automated Evaluation of Retrieval Augmented Generation*.
- Repositorio: fullstack-course.anthropic.com (sección RAG avanzado).

**Proyecto práctico:**
- Construye un pipeline RAG avanzado sobre los documentos técnicos de RIS Cajabamba (protocolos de atención, normativas MINSA). Compara: RAG básico vs. Hybrid Search + Reranking. Mide el recall y la faithfulness con Ragas en ambas versiones.

**Post de LinkedIn sugerido:**
> *"El RAG básico fallaba en el 30% de las preguntas sobre protocolos de salud. Implementé Hybrid Search + Reranker. Faithfulness subió de 0.71 a 0.93. Aquí la arquitectura completa."*

---

### Capítulo 22: Vector Databases en Producción

**Qué aprenderás:**
- El paisaje actual de bases de datos vectoriales: Pinecone, Qdrant, Milvus, Weaviate, Chroma y pgvector (extensión de PostgreSQL).
- Cómo funcionan internamente: algoritmos de búsqueda ANN (Approximate Nearest Neighbor) — diferencias entre HNSW (alta velocidad, alta precisión) vs. IVF (menor uso de RAM).
- **Multi-tenancy y control de acceso**: cómo garantizar que el agente de empresa A no recupere documentos de empresa B en el mismo índice vectorial (metadata filtering en la query).
- **Sincronización de datos**: cómo actualizar vectores cuando los documentos fuente cambian sin reconstruir todo el índice.
- Cuándo usar pgvector (ya tienes Postgres) vs. una base de datos vectorial dedicada: criterio de escala y latencia.

**Recursos recomendados:**
- Documentación oficial de Qdrant (la más completa para producción).
- Artículo: *"Choosing a Vector Database: A Comparison"* (Vicki Boykis, 2024).
- pgvector: github.com/pgvector/pgvector.

**Proyecto práctico:**
- Configura Qdrant localmente (Docker). Indexa los documentos normativos de MINSA en español. Implementa metadata filtering por tipo de documento y año. Compara los tiempos de búsqueda con 1,000 vs. 100,000 vectores y documenta la diferencia.

**Post de LinkedIn sugerido:**
> *"pgvector vs. Qdrant para sistemas de búsqueda semántica en salud pública. Cuándo el primero es suficiente y cuándo el segundo es inevitable. Benchmark con datos reales."*

---

### Capítulo 23: Fine-Tuning vs. Prompt Engineering — La Decisión Estratégica

**Qué aprenderás:**
- La regla de oro: **RAG corrige problemas de conocimiento. Fine-tuning corrige problemas de comportamiento.**
- Cuándo hacer fine-tuning: terminología de dominio muy específica, formato de salida rígido (JSON estructurado), tono institucional obligatorio.
- **LoRA (Low-Rank Adaptation)** y **QLoRA**: fine-tuning eficiente en parámetros de modelos open-weights (Llama 3, Mistral, Qwen) sin necesidad de hardware de nivel data center.
- **SFT (Supervised Fine-Tuning)** y **DPO (Direct Preference Optimization)**: cómo alinear el modelo a las preferencias del negocio y las restricciones de seguridad de la organización.
- Plataformas de fine-tuning gestionadas: Together.ai, Replicate, Fireworks.ai.
- Evaluación del modelo fine-tuneado: cómo demostrar que el modelo especializado supera al genérico en tu tarea concreta.

**Recursos recomendados:**
- Repositorio: microsoft/LoRA (paper original).
- Curso: Hugging Face PEFT documentation.
- Artículo: *"Fine-tuning vs. RAG: A Decision Framework"* (Hamel Husain).

**Proyecto práctico:**
- Aplica LoRA sobre un modelo Llama 3.2 (3B parámetros) para generar reportes de atenciones médicas en el formato oficial del MINSA Perú. Compara el output del modelo base vs. el fine-tuneado en 20 casos de prueba. Documenta el costo de tokens del enfoque de RAG vs. fine-tuning para el mismo volumen de consultas.

**Post de LinkedIn sugerido:**
> *"Fine-tuning un modelo de 3B parámetros para reportes del MINSA Perú. Costo, tiempo y resultado vs. RAG puro. La decisión no fue la que esperaba."*

---

### Capítulo 24: Orquestación Avanzada con LangGraph y Patrones Multi-Agente

**Qué aprenderás:**
- Por qué las cadenas lineales (LangChain chains) no sirven para flujos de trabajo empresariales con bucles, condicionales y estados persistentes.
- **LangGraph**: grafos de estado con ciclos para agentes que planifican, ejecutan herramientas, evalúan resultados y deciden si necesitan iterar.
- **Patrones de arquitectura multi-agente**:
  - *Supervisor / Router*: un agente orquestador que asigna tareas a agentes especializados (SQL agent, RAG agent, code executor).
  - *Parallel agents*: agentes independientes trabajando en simultáneo con reducción de resultados al final.
  - *Human-in-the-Loop (HITL)*: puntos de pausa donde el sistema espera aprobación humana antes de ejecutar una acción crítica (escribir en base de datos, enviar un email, ejecutar código en producción).
- **Gestión de estado y memoria**: estado de corto plazo en el thread de conversación vs. memoria de largo plazo en un vector store o grafo de conocimiento.
- Seguridad agéntica: cómo poner límites al agente para que no entre en bucles infinitos ni ejecute herramientas no autorizadas.

**Recursos recomendados:**
- Documentación oficial de LangGraph: langchain-ai.github.io/langgraph.
- Blog de Anthropic: *"Building Effective Agents"* (lectura obligatoria).
- Repositorio de ejemplos: github.com/langchain-ai/langgraph/tree/main/examples.

**Proyecto práctico:**
- Construye un sistema de análisis de datos multi-agente con LangGraph:
  1. **Agente Planificador**: recibe la pregunta del usuario y diseña el plan de análisis.
  2. **Agente SQL**: genera y ejecuta la consulta sobre tu base de datos de salud.
  3. **Agente Validador**: verifica que el resultado tiene sentido de negocio (detecta anomalías evidentes).
  4. **Agente Redactor**: formatea la respuesta final con contexto y recomendaciones.
  - Implementa HITL: si la query modifica datos, el sistema pausa y pide confirmación.

**Post de LinkedIn sugerido:**
> *"De una cadena lineal que fallaba en el 20% de las preguntas complejas a un grafo de 4 agentes con validación humana integrada. El patrón LangGraph que uso en producción."*

---

### Capítulo 25: LLMOps — Operaciones de IA en Producción Empresarial

**Qué aprenderás:**
- Diferencias entre MLOps clásico y LLMOps: no hay que entrenar modelos, el problema es gobernar, evaluar y optimizar el costo de sistemas que llaman APIs de LLMs.
- **Prompt versioning y CI/CD para prompts**: cómo tratar los prompts como código — versionarlos, testearlos con evaluaciones automáticas antes de cada despliegue y hacer rollback si el score baja.
- **Observabilidad full-stack**: trazar cada llamada al LLM con Langfuse, Phoenix o LangSmith — latencia por paso, costo de tokens por usuario/departamento, tasa de error y paso donde el agente falló.
- **Semantic caching**: cachear respuestas a preguntas semánticamente similares para reducir costos de API entre un 40-70% en consultas repetitivas.
- **Model routing y fallbacks**: enviar preguntas simples a modelos baratos (haiku, flash) y escalar a modelos fronteras solo cuando la complejidad lo justifica. Manejo de rate limits y caídas del proveedor.
- **Guardrails de seguridad**: prevenir prompt injection (entradas maliciosas del usuario que intentan cambiar el comportamiento del sistema), redacción de PII con Microsoft Presidio y filtros de salida con NeMo Guardrails o Llama Guard.
- **Optimización de costos en producción**: prompt compression, caching, batching de requests y selección del modelo correcto según la complejidad de la tarea.

**Recursos recomendados:**
- Langfuse: langfuse.com (open-source, auto-hosteable en Azure).
- Microsoft Presidio: github.com/microsoft/presidio (anonimización de PII).
- Artículo: *"The LLMOps Stack in 2025"* (Chip Huyen).
- *Designing Machine Learning Systems* (Chip Huyen) — Capítulos de producción y monitoreo.

**Proyecto práctico:**
- Implementa un stack de LLMOps completo sobre el sistema del Cap. 24:
  1. Conecta Langfuse para trazar todas las llamadas al LLM (latencia, tokens, costo).
  2. Implementa semantic caching con Redis.
  3. Agrega detección de PII con Presidio para que el sistema nunca loguee datos de pacientes.
  4. Crea un dashboard de operaciones que muestre: queries por día, costo acumulado, tasa de error y promedio de faithfulness por semana.

**Post de LinkedIn sugerido:**
> *"¿Cómo saben las empresas que su sistema de IA está funcionando bien en producción? Este es el stack de LLMOps que implementé: observabilidad, caching semántico y guardrails de PII. Números reales."*

---

## 🏢 Inteligencia Competitiva: ¿Qué Buscan las Mejores Empresas en 2026?

> Basado en job postings reales de Google, Meta, Anthropic, OpenAI y empresas tech de élite en Latinoamérica y España.

### El Perfil que Contrata el Mercado

El mercado dejó de buscar dos perfiles separados ("analista de datos" y "científico de datos"). El perfil que domina los job postings de 2025-2026 es el **AI Engineer con base sólida en datos**. Aquí el desglose:

| Skill | Frecuencia en JDs | Nivel Exigido |
| :--- | :--- | :--- |
| Python avanzado (async, type hints, testing) | ⭐⭐⭐⭐⭐ | Senior |
| SQL avanzado (Window Functions, query optimization) | ⭐⭐⭐⭐⭐ | Senior |
| RAG y Vector Databases | ⭐⭐⭐⭐⭐ | Mid-Senior |
| LLM APIs (OpenAI, Anthropic, Gemini) + multi-provider | ⭐⭐⭐⭐⭐ | Mid |
| Evals / LLM-as-a-Judge pipelines | ⭐⭐⭐⭐⭐ | Mid-Senior |
| Sistemas agénticos (LangGraph, CrewAI o custom) | ⭐⭐⭐⭐ | Mid-Senior |
| dbt / Analytics Engineering | ⭐⭐⭐⭐ | Mid |
| Docker + CI/CD (GitHub Actions) | ⭐⭐⭐⭐ | Mid |
| MCP / tool-use avanzado | ⭐⭐⭐⭐ | Mid-Senior |
| Azure / GCP / AWS (al menos uno a fondo) | ⭐⭐⭐⭐ | Mid |
| Fine-tuning con LoRA/QLoRA | ⭐⭐⭐ | Deseable |
| Seguridad en IA (prompt injection, guardrails, PII) | ⭐⭐⭐ | Mid-Senior |
| Observabilidad LLM (Langfuse, Phoenix, LangSmith) | ⭐⭐⭐ | Mid |
| Semantic Layer (dbt MetricFlow, Cube.js) | ⭐⭐⭐ | Deseable |

### Lo que Diferencia a un Candidato Top

**1. Portafolio de evidencia, no de certificados.**
Google, Anthropic y OpenAI no contratan por cantidad de cursos completados. Contratan por evidencia de que has construido algo real y lo has llevado a producción. Un repositorio de GitHub con un servidor MCP funcional, un pipeline de Evals automatizado y un sistema RAG con métricas documentadas pesa más que cualquier certificación.

**2. Capacidad de cuantificar resultados.**
"Mejoré el sistema de reportes" no funciona. "Reduje la latencia de las consultas de análisis de 40 segundos a 0.3 segundos mediante indexación cubriente y rediseño del plan de ejecución" sí funciona. Cada proyecto de este roadmap está diseñado para que tengas un número concreto que reportar.

**3. Comprensión de la economía de los LLMs.**
Las empresas que construyen productos con IA gastan millones de dólares en tokens. Los candidatos que entienden cómo optimizar ese costo (semantic caching, model routing, prompt compression) tienen una ventaja real sobre los que solo saben "hacer prompts".

**4. Ingeniería de confiabilidad, no demos.**
Anthropic lo dice explícitamente: no buscan demostraciones que funcionan una vez. Buscan sistemas con fallbacks definidos, evals que corren en CI/CD, guardrails que previenen comportamientos no deseados y observabilidad que muestra exactamente qué pasó cuando algo falló.

**5. Seguridad como primera clase.**
Prompt injection, exfiltración de datos sensibles vía el LLM, multi-tenancy en vector stores — estas no son consideraciones de "después del MVP". Las empresas que manejan datos sensibles (salud, finanzas, minería) contratan a ingenieros que integran seguridad desde el diseño.

### El Stack Técnico de Referencia 2026

```
📦 DATOS & TRANSFORMACIÓN
   └── dbt Core + MetricFlow (transformación + semantic layer)
   └── SQL Server / PostgreSQL / DuckDB
   └── Power BI + DAX Studio

🤖 AI ENGINEERING
   └── Python 3.12+ (async, typing, pytest)
   └── LLM APIs: Claude (Anthropic), GPT-4o (OpenAI), Gemini (Google)
   └── RAG: LlamaIndex / LangChain + Qdrant / pgvector
   └── Orquestación: LangGraph (multi-agent, HITL, stateful)
   └── Fine-tuning: LoRA/QLoRA con Hugging Face PEFT

🔌 CONECTIVIDAD
   └── MCP (Model Context Protocol) — clientes y servidores propios
   └── FastAPI (APIs de inferencia e integración)

📊 EVALS & OBSERVABILIDAD
   └── Ragas / DeepEval (métricas de sistemas RAG y agénticos)
   └── Langfuse (tracing y cost tracking en producción)
   └── GitHub Actions (CI/CD con evals automáticos)

🔒 SEGURIDAD
   └── Microsoft Presidio (anonimización de PII)
   └── NeMo Guardrails / Llama Guard (guardrails de output)
   └── Semantic caching con Redis

☁️ INFRAESTRUCTURA
   └── Docker + Azure Container Apps
   └── GitHub Actions (CI/CD)
   └── Kubernetes (nivel avanzado, deseable)
```

---

## 📊 Resumen del Mapa de Contenido LinkedIn (25 Posts de Autoridad)

| Cap | Gancho del Post | Pilar |
| :--- | :--- | :--- |
| 1 | El error más costoso en BI de salud: conectar Power BI directo a producción | Arquitectura del Dato |
| 2 | Query que tardaba 40 seg ahora tarda 0.3 seg — plan de ejecución antes/después | SQL Avanzado |
| 3 | Cómo modelé atenciones de 15 centros de salud en un esquema de estrella | Modelado Dimensional |
| 4 | Las 10 consultas de auditoría que corro antes de tocar cualquier base de datos | Calidad de Datos |
| 5 | dbt vs. stored procedures: la comparación práctica que le muestro a todo equipo | dbt Core |
| 6 | La arquitectura en capas que separa tu lógica de negocio de tus datos crudos | Staging / Marts |
| 7 | 15 tests automáticos que detectan datos corruptos antes de que rompan Power BI | Testing con dbt |
| 8 | Heredé 200 stored procedures sin documentar. Así reconstruí el linaje en 2 días | Linaje de Datos |
| 9 | 3 errores de DAX que hacen tu modelo 10x más lento | Power BI Avanzado |
| 10 | El archivo que le explica al agente de IA toda mi arquitectura desde el primer mensaje | AI-Native Workflow |
| 11 | Por qué los agentes de IA pierden el hilo en proyectos de datos largos y cómo lo resuelvo | Memoria en IA |
| 12 | MCP vs. RAG: cuál usar para conectar IA a bases de datos SQL | MCP |
| 13 | Construí un servidor MCP en 80 líneas que expone métricas de salud a cualquier asistente | MCP en Python |
| 14 | De 2 horas a 3 minutos: la skill que genera modelos dbt automáticamente | Skills Agénticas |
| 15 | 3 agentes trabajando en paralelo para migrar un pipeline ETL completo | Orquestación |
| 16 | Cómo la Capa Semántica de dbt eliminó las alucinaciones métricas de nuestro asistente | Semantic Layer |
| 17 | 5 problemas de seguridad que resolví antes de poner Text-to-SQL en producción | Text-to-SQL |
| 18 | Mi asistente tenía 73% de faithfulness. Qué hice para llegar al 91% | LLM Evals |
| 19 | Modelo que predice no-show de pacientes — ROC-AUC 0.84 y el hallazgo inesperado | ML de Negocio |
| 20 | El pipeline completo en producción: Docker + dbt CI/CD + observabilidad con Langfuse | DevOps de Datos |
| 21 | RAG básico fallaba en el 30% de mis preguntas. Hybrid Search + Reranker: 0.93 faithfulness | RAG Avanzado |
| 22 | pgvector vs. Qdrant para búsqueda semántica en salud. Benchmark con datos reales | Vector Databases |
| 23 | Fine-tuning un modelo de 3B para reportes MINSA. La decisión no fue la que esperaba | Fine-Tuning |
| 24 | De cadena lineal a grafo de 4 agentes con validación humana. El patrón LangGraph que uso | LangGraph Multi-Agent |
| 25 | El stack de LLMOps que implementé: observabilidad, caching semántico y guardrails de PII | LLMOps |

---

## 🗓️ Calendario de Ejecución Sugerido

| Semana | Capítulos | Publicaciones LinkedIn |
| :--- | :--- | :--- |
| 1-2 | Caps 1 y 2 | Posts 1 y 2 |
| 3-4 | Caps 3 y 4 | Posts 3 y 4 |
| 5-6 | Caps 5 y 6 | Posts 5 y 6 |
| 7-8 | Caps 7 y 8 | Posts 7 y 8 |
| 9-10 | Cap 9 | Post 9 |
| 11-12 | Caps 10 y 11 | Posts 10 y 11 |
| 13-14 | Caps 12 y 13 | Posts 12 y 13 |
| 15-16 | Caps 14 y 15 | Posts 14 y 15 |
| 17-18 | Caps 16 y 17 | Posts 16 y 17 |
| 19-20 | Cap 18 | Post 18 |
| 21-22 | Cap 19 | Post 19 |
| 23-24 | Cap 20 | Post 20 |
| 25-26 | Cap 21 | Post 21 |
| 27-28 | Cap 22 | Post 22 |
| 29-30 | Cap 23 | Post 23 |
| 31-32 | Cap 24 | Post 24 |
| 33-34 | Cap 25 | Post 25 |

> Al completar los 25 capítulos habrás construido: 3+ proyectos de portafolio en GitHub con métricas documentadas, 25 posts de autoridad técnica en LinkedIn, 1 servidor MCP propio, 1 sistema RAG avanzado con Evals, 1 orquestador multi-agente con LangGraph y todo el stack que buscan Google, Meta, Anthropic y OpenAI en sus AI Engineers. El perfil que el mercado de tecnología pagará mejor en 2026-2027.
