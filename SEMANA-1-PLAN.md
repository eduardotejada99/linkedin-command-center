# 🗓️ Plan de Publicación — Semana 1 (AI-First & High Authority)

**Objetivo:** Establecer posicionamiento como **AI-Augmented Engineer**, diferenciándote de los "vibe coders" y de los analistas tradicionales, demostrando experiencia en datos críticos (Salud y Minería) y maestría técnica en IA.

---

## 📝 Las 3 Publicaciones Listas para Publicar

### Publicación 1 (Martes 8:00 AM): Por qué el "Vibe Coding" colapsa en datos de producción
* **Fórmula de Gancho:** *Contrarian Take / Hot Topic 2026*
* **Tema:** Vibe Coding vs. AI-Augmented Engineering
* **Objetivo:** Abrir debate de alto nivel, atraer a CTOs y Data Leads que están lidiando con código roto generado por IA.

```text
El "vibe coding" es divertido para hacer prototipos en un fin de semana.

En datos de misión crítica, es una receta para el desastre.

En los últimos meses he visto a muchos programar tirando prompts a ciegas sin mirar el código que la IA genera.

El problema:
A un agente de IA no le importa si tu base de datos tiene duplicados silenciosos.
No sabe si tu JOIN generó un producto cartesiano que triplicó las cifras de ventas.
Y ciertamente no le importa si una consulta bloquea el servidor de producción.

En mi trabajo consolidando registros de salud pública y en telemetría de maquinaria minera, una métrica alucinada no es un bug visual: cuesta dinero real o decisiones sanitarias equivocadas.

La verdadera ventaja no es ser un "vibe coder" que copia y pega sin entender.
Es ser un ingeniero AI-Augmented:

- Usar agentes para acelerar la sintaxis y el boilerplate x5.
- Pero auditar cada consulta con rigor matemático y planes de ejecución (EXPLAIN).
- Blindar las tablas con tests automatizados y capas semánticas que la IA no pueda romper.

La IA escribe el código rápido.
El criterio de ingeniería garantiza que funcione en producción.

¿En tu equipo cómo están controlando la calidad del código generado por IA?
```

---

### Publicación 2 (Jueves 8:00 AM): Cómo evitar que un LLM alucine tus métricas (La Capa Semántica)
* **Fórmula de Gancho:** *Mechanism Reveal / Education*
* **Tema:** Text-to-SQL en la vida real y dbt Semantic Layer
* **Objetivo:** Mostrar dominio del Modern Data Stack aplicado a Inteligencia Artificial.

```text
Conectar ChatGPT directamente a una base de datos de tu empresa es el camino más rápido para obtener métricas inventadas.

La mayoría cree que Text-to-SQL es solo pasarle el schema de la base de datos al modelo y pedirle un query.

Lo que ocurre en la práctica:
- El usuario pregunta por "clientes activos".
- El LLM asume su propia definición de "activo" y filtra por fecha de creación.
- El departamento de finanzas usa otra definición.
- Tienes dos números distintos en la misma reunión de directorio.

La solución que adoptan los equipos AI-First modernos no es cambiar de modelo.
Es construir una Capa Semántica (Semantic Layer con herramientas como dbt o MetricFlow).

En lugar de dejar que el LLM consulte tablas crudas:
1. Defines la métrica "cliente_activo" una sola vez en código versionado.
2. Expones esa métrica a través de un servidor agéntico (como MCP).
3. El agente de IA no inventa SQL: consume la métrica validada con cero margen de alucinación.

La IA no necesita adivinar la lógica de tu negocio. Necesita que tu ingeniería de datos se la entregue estructurada.

¿Ya están probando asistentes de lenguaje natural sobre sus bases de datos internas?
```

---

### Publicación 3 (Viernes 8:30 AM): Lo que la telemetría en minería me enseñó sobre calidad de datos
* **Fórmula de Gancho:** *Before / After & Costo Operativo*
* **Tema:** Experiencia real en Piper Solutions (GoldFields, Veladero, Ambatovy)
* **Objetivo:** Credibilidad irrefutable de ingeniería pesada y manejo de grandes flujos de datos.

```text
En una mina a tajo abierto, cada minuto que una pala hidráulica pasa detenida cuesta miles de dólares.

Cuando trabajé desarrollando backend en Python para sistemas de telemetría de paradas operativas (downtimes) en mineras internacionales, me grabé una regla a fuego:

La calidad de un dato se mide en el momento de la ingesta, no en el dashboard final.

Teníamos flujos continuos de sensores enviando estados de maquinaria pesada.
Si un proceso de ingesta fallaba o registraba un evento desfasado, los reportes de mantenimiento preventivo quedaban inutilizables para la guardia de operaciones.

Tuvimos que diseñar pipelines con tres principios:
1. Estados atómicos: nunca asumir que un sensor envió el paquete en orden cronológico perfecto.
2. Procesamiento asíncrono en la nube para que picos de tráfico no congelaran la base de datos.
3. Consultas optimizadas con particiones temporales estrictas.

Hoy veo a muchos equipos queriendo aplicar modelos predictivos complejos sobre datos que ni siquiera llegan limpios de origen.

No hay modelo de Machine Learning que compense una ingesta defectuosa.
Primero resuelve la tubería. Luego construye la inteligencia.

¿Cuál ha sido el entorno más exigente en tiempo real donde te ha tocado procesar datos?
```

---

## 🎯 Plan de Acción de Networking (15 minutos al día)

Usa la skill `li-comment` para comentar en posts de líderes técnicos en estos 3 nichos:

| Día | Acción | Herramienta |
| :--- | :--- | :--- |
| **Lunes** | Dejar 3 comentarios técnicos en publicaciones sobre dbt o Modern Data Stack | `li-comment` |
| **Martes** | Publicar Post 1 + Responder cada comentario recibido en la primera hora | `post-writer` + `li-reply` |
| **Miércoles** | Enviar 2 notas de conexión a Data Leads de empresas target | `li-dm` |
| **Jueves** | Publicar Post 2 + Dejar 3 comentarios en posts sobre IA aplicada | `post-formatter` + `li-comment` |
| **Viernes** | Publicar Post 3 + Triaje de mensajes entrantes | `li-inbox` |
