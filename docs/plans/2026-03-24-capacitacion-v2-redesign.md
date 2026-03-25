# Capacitacion Docentes v2 — Interactive Learning Experience

**Date:** 2026-03-24
**Status:** In review
**Principle:** The training must MODEL what we teach. If we preach retrieval practice, the training does retrieval practice. If we preach active learning, the training IS active learning.

---

## Architecture: Step-Based Micro-Learning

Instead of "slides + narration", each module is a sequence of **steps**. Each step is ONE of these types:

### Step Types

| Type | Icon | Description | Duration |
|------|------|-------------|----------|
| `video` | 🎬 | Embedded video (Google Drive, YouTube) | 1-5 min |
| `content` | 📖 | Rich text/images — explanation with screenshots | 2-3 min reading |
| `quiz` | 🧠 | Multiple choice with immediate feedback | 1-2 min |
| `practice` | 💻 | "Go to the platform and do X" with checklist | 5-15 min |
| `reflection` | 💬 | Open-ended question, teacher writes response (saved locally) | 2-5 min |
| `screenshot` | 📸 | Full-width annotated platform screenshot with callouts | 1 min |

### Flow per Module (~45-60 min each)

```
VIDEO → CONTENT → QUIZ → PRACTICE → SCREENSHOT → QUIZ → REFLECTION
```

No passive narration. No TTS. Real videos, real screenshots, real interaction.

---

## Content Inventory (What We Have)

### Videos
- Jaime Saavedra Welcome: `1epEU4vQEa4nxbwcHkuKG1mz8KBtSpIfe`
- Demo Tutor IA Math: `1Je8uRcmj3mQZp_KzbHjMvPvC4SpkqdxL`
- Demo Coach IA OV: `1cY-CvrgCDIBztI9OUuI8lHwJnV-okw-1`

### Platform Access
- URL: `eligiendomicamino.portal.udocz.com`
- Test student: DNI 5000003000 / password 5000003000
- Screenshots captured: portal, Doc chat, question view, wrong answer feedback, Modo Escuela, OV dashboard, 8 pasos

### Guides
- Guia Docente Matematicas: `12Q5zUjofNHHfONZT2nSSQVOGH8M2zuan`
- Guia del Tutor OV: `1_KfUBZ2gCql4iFDlv1UqFKSyBGpBl_GF`

### Slides
- Math Day 1: `1V_ID56Czrnv0XfMCQTO8rutsnJ4Fb4-ePGe7GYoDuOU`
- Math Day 2: `1eYwrDWsaJF6v7fXVCQiCpf5uCspyXltIYHyvxYPw9lU`
- OV M1-M6: 6 separate presentations

---

## Math Track — 5 Modules (~4-5 hours total)

### Modulo 1: Bienvenida y Contexto (~45 min)

**Step 1 — VIDEO: Jaime Saavedra Welcome** (3 min)
- Embed: `1epEU4vQEa4nxbwcHkuKG1mz8KBtSpIfe`

**Step 2 — CONTENT: ¿Qué es Eligiendo Mi Camino?**
- DRELM + Banco Mundial + UPC partnership
- 100 schools, 6,600 students, 200 teachers, 16 weeks
- Your role: you're the human piece — AI handles practice, you handle understanding
- Screenshot of the portal showing both tracks

**Step 3 — QUIZ: Verifica tu comprensión**
- Q1: "¿Cuántas escuelas participan en el piloto?" → a) 50 b) 100 c) 200 d) 500
  - Feedback correct: "¡Exacto! 100 escuelas de Lima Metropolitana"
  - Feedback wrong: "Son 100 escuelas. Recuerda: 100 escuelas, 6,600 estudiantes, 200 docentes"
- Q2: "¿Cuál es tu rol principal como docente en este programa?" → a) Reemplazar la IA b) Enseñar programación c) Construir comprensión y motivación d) Supervisar la tecnología
  - Feedback: "Tu rol es construir comprensión, motivación y vínculo humano. La IA se encarga de la práctica repetitiva."
- Q3: "¿Cuántas horas semanales de laboratorio tendrán los estudiantes?" → a) 1 b) 2 c) 4 d) 6

**Step 4 — CONTENT: ¿Qué es la Inteligencia Artificial?**
- A language model predicts the next word — no consciousness, no emotions
- What AI CAN do vs CANNOT do (table)
- 4 myths debunked with explanations

**Step 5 — QUIZ: 4 Mitos — ¿Verdadero o Falso?**
- "La IA va a reemplazar al docente" → F (feedback explains why)
- "La IA siempre da respuestas correctas" → F (hallucinations)
- "Los estudiantes necesitan saber programar" → F (chat interface)
- "Solo profes tecnológicos pueden hacer esto" → F (WhatsApp analogy)

**Step 6 — PRACTICE: Prueba una IA tú mismo**
- Instructions: "Abre ChatGPT, Claude, o Copilot en tu celular. Hazle esta pregunta: 'Si un pantalón cuesta S/100 y primero sube 20%, luego baja 20%, ¿cuánto cuesta al final?' Evalúa la respuesta."
- Checklist: [ ] Abrí una IA, [ ] Hice la pregunta, [ ] La respuesta fue correcta (S/96), [ ] Entendí por qué no es S/100

**Step 7 — REFLECTION: Tu primera impresión**
- "¿Qué te sorprendió de la respuesta de la IA? ¿Crees que un estudiante de 5to la entendería?"

### Modulo 2: La Plataforma Doc (~60 min)

**Step 1 — VIDEO: Demo del Tutor IA** (5 min)
- Embed: `1Je8uRcmj3mQZp_KzbHjMvPvC4SpkqdxL`

**Step 2 — RETRIEVAL: ¿Qué recuerdas del Módulo 1?**
- Q1: "¿Qué hace un modelo de lenguaje?" → Predice la siguiente palabra
- Q2: "¿Cuál es la diferencia entre lo que hace la IA y lo que haces tú?" → IA: práctica repetitiva. Tú: comprensión y motivación

**Step 3 — CONTENT: Conoce a Doc**
- Doc = tutor IA de matemáticas by uDocz, powered by Claude (Anthropic)
- Método socrático: pista 1 → pista 2 → explicación completa
- SCREENSHOT: Doc chat greeting with 3 modes
- SCREENSHOT: Question view (√49 with 4 options)

**Step 4 — CONTENT: El poder diagnóstico**
- 4,000+ diagnostic questions
- Each wrong answer → specific conceptual error identified
- SCREENSHOT: Wrong answer feedback showing "Error conceptual" + "Remediación"
- This is what makes Doc different from a textbook

**Step 5 — QUIZ: ¿Cómo funciona Doc?**
- Q1: "Cuando un estudiante se equivoca, Doc..." → a) Le da la respuesta b) Le dice que está mal c) Identifica el error conceptual específico y hace una pregunta de remediación d) Le pone una mala nota
- Q2: "¿Cuántas preguntas diagnósticas tiene el banco?" → ~4,000
- Q3: "El método socrático significa que Doc..." → a) Da clases magistrales b) Guía con preguntas progresivas sin dar la respuesta directa c) Evalúa con exámenes d) Reemplaza al docente

**Step 6 — CONTENT: Modo Escuela vs Modo Casa**
- SCREENSHOT: Welcome screen showing both modes
- Modo Escuela (Model B): structured, system-controlled, "Apertura de recuperación"
- SCREENSHOT: Modo Escuela question view
- Modo Casa (Model A): 4 modes — Aprender, Resolver, Ponte a prueba, Preguntar
- SCREENSHOT: Topic selection with Competencia 1 & 2

**Step 7 — PRACTICE: Explora la plataforma como estudiante**
- "Abre eligiendomicamino.portal.udocz.com. Usa DNI: [tu DNI de prueba] y contraseña: [tu contraseña]."
- "Haz click en 'Comenzar mi práctica' (Matemáticas)"
- "Selecciona Modo Casa → elige Tema 1 → Ponte a prueba → Números irracionales"
- "Resuelve 3 preguntas. EQUIVÓCATE A PROPÓSITO en al menos una para ver cómo Doc te da feedback."
- Checklist: [ ] Ingresé a la plataforma, [ ] Resolví preguntas en Modo Casa, [ ] Me equivoqué a propósito, [ ] Vi el "Error conceptual" y la "Remediación", [ ] Entendí cómo Doc diagnostica errores

**Step 8 — QUIZ: Después de usar la plataforma**
- Q1: "Cuando te equivocaste, ¿qué te mostró Doc?" → Error conceptual + pregunta de remediación
- Q2: "¿Qué opción te permite elegir el tema libremente?" → Modo Casa
- Q3: "En Modo Escuela, ¿qué pasa al inicio de cada sesión?" → Apertura de recuperación (repaso de sesión anterior)

### Modulo 3: Registro, Currículo y Dashboard (~50 min)

**Step 1 — RETRIEVAL: ¿Qué recuerdas?**
- Q1: "¿Cuántos modos tiene Modo Casa?" → 4 (Aprender, Resolver, Ponte a prueba, Preguntar)
- Q2: "¿Qué es la 'Apertura de recuperación'?" → Repaso de la sesión anterior al inicio de Modo Escuela

**Step 2 — CONTENT: Registro de estudiantes**
- Roster format: DNI, nombres completos, sección
- Mass account activation: DNI = username = initial password
- Password protocol: distribution → student changes → recovery → escalation
- Pre-launch verification: test ALL logins before day 1

**Step 3 — CONTENT: Integración curricular**
- 4h/week schools: 2h classroom + 2h lab
- 6h/week schools: 4h classroom + 2h lab
- CNEB competencies: C1 (Cantidad) + C2 (Regularidad) covered by platform
- Topics 1-11 mapped to 5to curriculum
- SCREENSHOT: Topic selection showing all themes

**Step 4 — QUIZ: Logística**
- Q1: "Si tu colegio tiene 4 horas semanales de matemáticas, ¿cómo se distribuyen?" → 2h aula + 2h lab
- Q2: "¿Qué competencias cubre la plataforma?" → C1 y C2
- Q3: "¿Cuál es la contraseña inicial de cada estudiante?" → Su DNI

**Step 5 — CONTENT: Dashboard del docente**
- Real-time metrics: active students, topic per student, stuck students
- Resolution categories: solved alone, with help, AI solved, not solved
- SCREENSHOT: Dashboard view (when available)
- The dashboard tells you what to teach NEXT in the classroom

**Step 6 — PRACTICE: Planifica tu primera semana**
- "Descarga la plantilla de planificación semanal"
- "Completa: ¿Qué tema cubrirás en el aula? ¿Qué tema asignarás en la plataforma?"
- "¿Tu colegio tiene 4h o 6h semanales? Ajusta tu plan."
- Checklist: [ ] Identifiqué mi carga horaria, [ ] Elegí los primeros 4 temas, [ ] Definí qué va en aula y qué en lab

### Modulo 4: Gestión de Aula con IA (~60 min)

**Step 1 — RETRIEVAL**
- Q1: "¿Qué categorías de resolución muestra el dashboard?" → Resolvió solo, con ayuda mínima, IA lo resolvió, no resolvió
- Q2: "¿Qué haces si un estudiante olvida su contraseña?" → Protocolo de recuperación → escalación a coordinador

**Step 2 — CONTENT: El Modelo de 5 Momentos**
- Apertura (5 min): seating, login, verify topic
- Práctica autónoma (35-40 min): students with Doc, teacher circulates
- Pausa / Discusión (10-15 min): common error from dashboard
- Segunda ronda (20-25 min): students continue
- Cierre (5-10 min): summary, preview next session

**Step 3 — CONTENT: 3 Tipos de Circulación**
- Escaneo (5-10 min): scan all screens
- Inmersión (3 students, ~90 sec each): deeper check
- Intervención agrupada (3+ students same issue): pull aside

**Step 4 — QUIZ: ¿Qué harías?**
- Scenario 1: "Un estudiante dice 'esto es aburrido' y cierra la laptop" → a) Lo regañas b) Le pides 10 minutos más sin presión c) Lo ignoras d) Lo mandas a dirección → Feedback: approach calmly, ask for 10 minutes
- Scenario 2: "3 estudiantes tienen el mismo error en fracciones" → a) Das una clase magistral de 20 min b) Intervención agrupada: los juntas 3 min para aclarar c) Los ignoras d) Les das la respuesta
- Scenario 3: "Un estudiante termina rápido todas las preguntas" → a) Le dices que espere b) Le asignas otro tema c) Le pides que ayude a un compañero d) b y c

**Step 5 — CONTENT: Qué NO hacer**
- DON'T sit at desk the whole session
- DON'T give long lectures mid-session
- DON'T give answers when student is frustrated
- DON'T interrupt B' retrieval practice
- DON'T repurpose lab time for other activities

**Step 6 — VIDEO: Simulación de sesión (embedded slides section)**
- Use slides for the simulation walkthrough
- The S/100 pantalón example (+20% then -20% = S/96)

**Step 7 — PRACTICE: Simula una sesión**
- "Imagina que estás en tu laboratorio. Tienes 25 estudiantes."
- "Minuto 0-5: ¿Qué haces? (Apertura)"
- "Minuto 5-40: ¿Qué observas en las pantallas? ¿Cuándo intervienes?"
- "Minuto 40-50: Abres el dashboard y ves que 8 estudiantes tienen el mismo error en porcentajes. ¿Qué haces?"
- "Minuto 50-55: Cierre. ¿Qué les dices?"

**Step 8 — REFLECTION**
- "¿Cuál de los 3 tipos de circulación te parece más difícil? ¿Por qué?"

### Modulo 5: Acompañamiento, Evaluación y Plan (~45 min)

**Step 1 — RETRIEVAL**
- Q1: "Nombra los 5 momentos de una sesión de lab"
- Q2: "¿Qué tipo de circulación usas cuando 3+ estudiantes tienen el mismo error?"

**Step 2 — CONTENT: El diseño experimental B vs B'**
- Model B: standard AI tutoring
- Model B': 3 enhancements (retrieval practice, predict/reveal/diagnose, planted errors)
- CRITICAL: do NOT intervene during B' modifications
- You need to know which arm your school is in

**Step 3 — CONTENT: Tu red de apoyo**
- WhatsApp group per UGEL
- Training team observation visits (supportive, not evaluative)
- PIP coordinator in your school
- Evaluation calendar: baseline (week 1), midterm (May), final (June/July)

**Step 4 — QUIZ: Evaluaciones**
- Q1: "¿Cuántas evaluaciones hay?" → 3 (baseline, midterm, final)
- Q2: "¿Las visitas de observación son evaluativas?" → No, son de acompañamiento
- Q3: "Si tu escuela es del grupo B', ¿debes intervenir durante la apertura de recuperación?" → No

**Step 5 — PRACTICE: Tu plan de acción**
- Pre-launch checklist with checkboxes
- "Completa tu plan de 4 semanas"
- "Guarda los contactos de soporte en tu celular"

**Step 6 — REFLECTION: Carta a ti mismo/a**
- "Escribe 3 compromisos que te haces como docente de este programa"
- "¿Cuál es tu mayor preocupación? Compártela en el grupo de WhatsApp."

---

## OV Track — 5 Modules (~4-5 hours total)

(Same structure — video → content → quiz → practice → reflection. Uses OV videos, OV guide content, OV platform screenshots.)

### Modulo 1: Bienvenida, Tu Rol y el Estudiante (~50 min)
### Modulo 2: IA y el Programa de 8 Pasos (~55 min)
### Modulo 3: Herramientas y Preparación (~50 min)
### Modulo 4: Facilitación y Situaciones Difíciles (~55 min)
### Modulo 5: Acompañamiento, Evaluación y Compromiso (~45 min)

(Detailed step content to be written based on Guía del Tutor OV)

---

## Technical Architecture

### Step Renderer
Each step type has its own renderer:

```javascript
const STEP_RENDERERS = {
  video: (step) => `<div class="step-video"><iframe src="...preview"></iframe></div>`,
  content: (step) => `<div class="step-content">${step.html}</div>`,
  quiz: (step) => renderQuiz(step.questions),
  practice: (step) => renderPractice(step.instructions, step.checklist),
  reflection: (step) => renderReflection(step.prompt),
  screenshot: (step) => renderScreenshot(step.src, step.caption, step.callouts)
};
```

### Quiz Engine
- Multiple choice with immediate feedback
- Shows correct/incorrect with explanation
- No score/grade — purely formative
- Tracks completion in localStorage

### Practice Checklist
- Interactive checkboxes
- "I did this" confirmation before moving on
- Links to external resources (platform URL, downloads)

### Progress
- localStorage tracks: completed steps, completed modules, reflection responses
- Progress bar per module
- "Recomendamos hacer 1 módulo por día" banner (not blocking)

### No TTS
- Videos replace narration
- Content is READ, not listened to
- Rich formatting with screenshots inline

---

## Design Decisions

- **No TTS** — browser TTS quality is insufficient for professional training. Use real videos + rich text.
- **Formative quizzes** — no grades, immediate feedback, retrieval practice principle
- **Spacing recommended** — banner suggests 1 module/day but doesn't block
- **Platform practice required** — can't skip practice steps (must check all items)
- **Screenshots embedded** — not in an img/ folder, use base64 or hosted URLs
- **Mobile-friendly** — teachers will do this on phones too
