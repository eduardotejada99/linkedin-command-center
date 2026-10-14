# 🚀 LinkedIn Command Center & AI-First Career Hub

> Centro de control integral para posicionamiento profesional, automatización de contenidos en LinkedIn y roadmap técnico hacia roles de **Senior Analytics Engineer** y **Applied AI Specialist**.

**Propietario:** Eduardo Tejada Reyes  
**Credenciales:** Ingeniero de Sistemas Colegiado (CIP: 372629) | 1er Puesto de Promoción (UPN) | Maestría en Inteligencia Artificial (UNIR - En curso)  
**Enfoque:** Arquitectura de datos de misión crítica (Python, SQL Server, PostgreSQL, dbt, Azure) y Sistemas de Datos AI-First (Semantic Layers, Text-to-SQL, MCP, LLM Evals).

---

## 🗂️ Arquitectura del Repositorio

| Archivo | Propósito |
| :--- | :--- |
| **[`CONTEXTO-MAESTRO.md`](./CONTEXTO-MAESTRO.md)** | **Single Source of Truth:** Lee este archivo al iniciar cualquier conversación con un agente de IA para tener 100% del contexto sin repetir nada. |
| **[`PERFIL-LINKEDIN-OPTIMIZADO.md`](./PERFIL-LINKEDIN-OPTIMIZADO.md)** | Textos definitivos de copia y pega para tu LinkedIn (Titulares en ES/EN, Acerca de en ES/EN, Experiencias y Destacados). |
| **[`ROADMAP-CARRERA.md`](./ROADMAP-CARRERA.md)** | Ruta técnica 2026: Modern Data Stack, dbt Semantic Layer, agentes Text-to-SQL, MCP y estrategia de empleo. |
| **[`SEMANA-1-PLAN.md`](./SEMANA-1-PLAN.md)** | Plan de publicación semanal: 3 publicaciones listas (Vibe coding vs Ingeniería, Capa Semántica y Telemetría minera) + targets de networking. |
| **[`LINKEDIN-PLAYBOOK.md`](./LINKEDIN-PLAYBOOK.md)** | Catálogo y manual de uso de las skills de IA (`post-writer`, `li-plan`, `li-comment`, `li-dm`, `li-human`). |
| **[`voice.md`](./voice.md)** & **[`about-me.md`](./about-me.md)** | Archivos de calibración de voz y pilares temáticos para agentes generadores de contenido. |
| **[`tools/`](./tools/)** | Scripts offline en Python (`detect.py`, `humanize.py`, `slop.json` y `hooks.json` con 21 fórmulas de ganchos). |

---

## 🛠️ Herramientas CLI Incluidas (`tools/`)

Herramientas estándar sin librerías externas que puedes ejecutar en cualquier terminal (Windows, Linux, Mac):

```bash
# 1. Limpiar un borrador eliminando caracteres invisibles y em dashes
python tools/humanize.py mi_post.txt --report

# 2. Evaluar el score de detección de IA (0 a 100)
python tools/detect.py mi_post.txt

# 3. Comparar un antes y después
python tools/detect.py antes.txt despues.txt
```

---

## 🌐 Cómo usar este repositorio en cualquier IA

Cuando inicies una nueva conversación en **Antigravity IDE**, **Claude Code**, **ChatGPT** o cualquier otro asistente, simplemente dile:

> *"Por favor lee el archivo `CONTEXTO-MAESTRO.md` de mi repositorio `https://github.com/eduardotejada99/linkedin-command-center` para conocer mi perfil profesional, voz y objetivos antes de empezar."*

El agente absorberá instantáneamente todo tu contexto sin necesidad de que vuelvas a explicar tu CV ni tu trayectoria.
