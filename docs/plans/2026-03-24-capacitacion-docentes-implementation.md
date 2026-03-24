# Capacitacion Docentes — Implementation Plan

> **For Claude:** REQUIRED SUB-SKILL: Use superpowers:executing-plans to implement this plan task-by-task.

**Goal:** Build a self-paced interactive training app for teachers who missed the EMC math and OV training, with embedded slides and conversational Spanish narration.

**Architecture:** Single-page vanilla HTML/CSS/JS app (same pattern as bienvenida-docentes). All views managed by JS state. Google Slides embedded via iframe. Narration in collapsible sections below slides. Progress tracked in localStorage.

**Tech Stack:** HTML5, CSS3 (custom properties, grid, flexbox), vanilla JS, Google Fonts (Montserrat), Font Awesome icons, GitHub Pages hosting.

---

## Task 1: Create Repo and App Shell

**Files:**
- Create: `index.html`

**Step 1: Create the GitHub repo**

```bash
cd C:\Users\cosmo\Downloads
mkdir capacitacion-docentes
cd capacitacion-docentes
git init
```

**Step 2: Write the HTML shell with all CSS and view framework**

Create `index.html` with:

1. **Head:** Meta viewport, Montserrat font, Font Awesome CDN, all CSS in `<style>` tag
2. **CSS variables** matching bienvenida-docentes branding:
   ```css
   :root {
     --primary: #f39300;
     --primary-dark: #f75a00;
     --primary-light: #fdd026;
     --bg-cream: #fffbf0;
     --text-dark: #242c32;
     --text-gray: #666;
     --math-color: #C62828;
     --math-bg: #FFEBEE;
     --ov-color: #2E7D32;
     --ov-bg: #E8F5E9;
     --card-shadow: 0 2px 12px rgba(0,0,0,0.08);
     --radius: 12px;
   }
   ```
3. **Three view containers** (only one visible at a time):
   - `#landing` — Track selection (Matemáticas / Orientación Vocacional)
   - `#modules` — Module list for selected track
   - `#viewer` — Slide embed + narration panel
4. **JS state management:**
   ```javascript
   const state = { view: 'landing', track: null, moduleId: null };
   function navigate(view, opts) { ... } // updates state, toggles visibility
   ```
5. **localStorage progress helpers:**
   ```javascript
   function getProgress() { return JSON.parse(localStorage.getItem('emc-cap-progress') || '{}'); }
   function markComplete(track, moduleId) { ... }
   function isComplete(track, moduleId) { ... }
   ```

**Step 3: Build the Landing Page view**

- Hero section: Orange gradient background, EMC logo, title "Capacitación Docente", subtitle "Formación virtual para docentes de Eligiendo Mi Camino"
- Partner badges row: DRELM, Banco Mundial, UPC, uDocz (same as bienvenida-docentes)
- Two large track cards:
  - **Matemáticas** (red accent, calculator icon): "Día 1 y Día 2 de formación — Aprende a usar el tutor IA de matemáticas Doc en tu aula"
  - **Orientación Vocacional** (green accent, compass icon): "6 módulos — Prepárate para guiar a tus estudiantes con el coach vocacional IA"
- Each card shows progress bar (X/N módulos completados) from localStorage
- Click → `navigate('modules', { track: 'math' })` or `navigate('modules', { track: 'ov' })`

**Step 4: Build the Module List view**

- Back arrow → landing
- Track header with color accent
- Grid of module cards, each showing:
  - Module number and title
  - Short description (1 line)
  - Duration estimate
  - Completion badge (checkmark if done)
  - Click → `navigate('viewer', { track, moduleId })`

**Step 5: Build the Viewer view**

- Back arrow → module list
- Module title bar with track color
- Google Slides iframe (full width, 60vh):
  ```html
  <iframe src="https://docs.google.com/presentation/d/{ID}/embed?start=false&loop=false&delayms=60000"
    frameborder="0" width="100%" height="100%" allowfullscreen="true"></iframe>
  ```
- Narration panel below (40vh, scrollable):
  - Collapsible sections with `<details><summary>` elements
  - Each section has `data-audio-slot` attribute for future audio
  - Content: narration text for that block
- Resources section: links to guide PDF, slides folder
- "Marcar como completado" button at bottom
- Prev/Next module navigation

**Step 6: Commit**

```bash
git add index.html
git commit -m "feat: app shell with landing, module list, and viewer views"
```

---

## Task 2: Module Data and Configuration

**Files:**
- Modify: `index.html` (add JS data)

**Step 1: Add module data object**

Inside the `<script>` tag, add the complete module configuration:

```javascript
const MODULES = {
  math: {
    title_es: "Matemáticas",
    title_en: "Mathematics",
    color: "var(--math-color)",
    bg: "var(--math-bg)",
    icon: "fa-calculator",
    guideUrl: "https://drive.google.com/file/d/12Q5zUjofNHHfONZT2nSSQVOGH8M2zuan/view?usp=sharing",
    folderUrl: "https://drive.google.com/drive/folders/1kfWgFFFpGl9LDKlUhREi9cBjERI2BJm3",
    slidesFolder: "https://drive.google.com/drive/folders/1h_I1p-dcWMnMM8__eAFuV_vjkNkMEkO-",
    modules: [
      {
        id: "dia1",
        title: "Día 1 — Bienvenida, Plataforma y Currículo",
        desc: "IA, plataforma Doc, registro, integración curricular y dashboard",
        duration: "~90 min de lectura",
        embedId: "1V_ID56Czrnv0XfMCQTO8rutsnJ4Fb4-ePGe7GYoDuOU",
        blocks: [ /* narration blocks added in Task 3 */ ]
      },
      {
        id: "dia2",
        title: "Día 2 — Gestión de Aula y Plan de Acción",
        desc: "Diseño experimental, gestión de sesiones, simulación y plan individual",
        duration: "~90 min de lectura",
        embedId: "1eYwrDWsaJF6v7fXVCQiCpf5uCspyXltIYHyvxYPw9lU",
        blocks: [ /* narration blocks added in Task 3 */ ]
      }
    ]
  },
  ov: {
    title_es: "Orientación Vocacional",
    title_en: "Career Guidance",
    color: "var(--ov-color)",
    bg: "var(--ov-bg)",
    icon: "fa-compass",
    guideUrl: "https://drive.google.com/file/d/1_KfUBZ2gCql4iFDlv1UqFKSyBGpBl_GF/view?usp=sharing",
    folderUrl: "https://drive.google.com/drive/folders/1m_OnilfgQSEJusmA3nz9Xk8-hcq8rsVo",
    slidesFolder: "https://drive.google.com/drive/folders/1tZWTL0cRKIunBRbaH3bFrK2g34WcW-ir",
    modules: [
      { id: "m1", title: "Módulo 1 — Bienvenida y Contexto", desc: "Qué es EMC, tu rol como tutor/a, manifiesto", duration: "~45 min", embedId: "11h97scJhZ9gOJETm4xH71MaB45bAeq0v" },
      { id: "m2", title: "Módulo 2 — Alfabetización en IA", desc: "Qué es IA, qué puede y no puede hacer, protocolo de alerta", duration: "~45 min", embedId: "1FHOp5UZ-1tZ9663v8TMuXzSOpFy-tuYE" },
      { id: "m3", title: "Módulo 3 — El Programa", desc: "12 sesiones, 8 pasos, estructura y plataforma", duration: "~60 min", embedId: "1NdvFA8KHBqC7ylinv88MNBgeKpmY3D5o" },
      { id: "m4", title: "Módulo 4 — Herramientas", desc: "Plataforma, NotebookLM, diario digital, fichas", duration: "~60 min", embedId: "1tQiMK_JG-vdaSf2E3Ra2VTkBMHTdsEyG" },
      { id: "m5", title: "Módulo 5 — Práctica y Fricción", desc: "Simulación de sesión, situaciones difíciles", duration: "~45 min", embedId: "1Oj1zJ6pVGW3jySS5NleCfURf0Pmw_bKQ" },
      { id: "m6", title: "Módulo 6 — Compromiso y Cierre", desc: "Plan de acción, red de apoyo, próximos pasos", duration: "~30 min", embedId: "1YGWLaQVS-GoGWO1jYincqIpS_JVklndD" }
    ]
  }
};
```

**Step 2: Wire data to views**

Update the module list renderer and viewer to read from MODULES object.

**Step 3: Commit**

```bash
git add index.html
git commit -m "feat: add module data configuration for math and OV tracks"
```

---

## Task 3: Math Track Narration — Day 1

**Files:**
- Modify: `index.html` (add narration blocks to math.modules[0].blocks)

Write conversational Spanish narration for Day 1 (5 blocks). Each block is an object:

```javascript
{ title: "Bloque 1: Bienvenida y contexto", slideRange: "Diapositivas 1-4", content: "..." }
```

### Block content (based on Guía Docente + slide analysis):

**Bloque 1 — Bienvenida, contexto y alfabetización en IA (Diapositivas 1-10)**
Narration covers: What is EMC, the 3 partners (DRELM/BM/UPC), 100 schools / 6,600 students / 200 teachers, what AI is and isn't, 4 myths debunked, hands-on activity prompt (test ChatGPT with a math question). Include platform screenshot references where relevant.

**Bloque 2 — Conociendo la plataforma como estudiante (Diapositivas 11-22)**
Narration covers: Meet "Doc" the math tutor, Socratic method with progressive hints, 4,000 diagnostic questions, Modo Escuela vs Modo Casa, hands-on activity (log in and deliberately make errors). Reference platform screenshots.

**Bloque 3 — Registro de estudiantes y logística (Diapositivas 23-28)**
Narration covers: Student roster format, mass account activation, password protocol (distribution + recovery + escalation), pre-launch verification session, checklist.

**Bloque 4 — Integración curricular (Diapositivas 29-31)**
Narration covers: 4h vs 6h weekly programs, CNEB competency mapping (C1-C4), which topics are available on platform, schedule planning exercise.

**Bloque 5 — Dashboard del docente (Diapositivas 32-38)**
Narration covers: Real-time dashboard navigation, resolution categories (solved alone, with help, AI solved, not solved), frequent error analysis, simulated data exercise, 3-2-1 closing reflection.

**Step: Commit**

```bash
git commit -m "feat: add math day 1 narration (5 blocks)"
```

---

## Task 4: Math Track Narration — Day 2

**Files:**
- Modify: `index.html` (add narration blocks to math.modules[1].blocks)

Write conversational Spanish narration for Day 2 (5 blocks):

**Bloque 6 — El diseño experimental B vs B' (Diapositivas 1-5)**
Narration covers: Recap quiz, 3 B' modifications (retrieval practice, predict/reveal/diagnose, planted errors), live demo experience, why teachers must NOT intervene during B' modifications.

**Bloque 7 — Gestión del aula (Diapositivas 6-12)**
Narration covers: 5-moment session model (opening 5min, autonomous 35-40min, pause 10-15min, second round 20-25min, closure 5-10min), 3 circulation types (scanning, immersion, grouped), common situations table, role-play activity.

**Bloque 8 — Simulación de sesión completa (Diapositivas 13-18)**
Narration covers: 40-minute modeling session, teacher-as-student experience, debrief protocol, do's and don'ts, platform vs teacher roles.

**Bloque 9 — Acompañamiento y evaluaciones (Diapositivas 19-22)**
Narration covers: WhatsApp support network by UGEL, in-school observation visits, evaluation calendar (baseline week 1, midterm May, final June).

**Bloque 10 — Plan de acción y cierre (Diapositivas 23-30)**
Narration covers: Pre-launch checklist, 4-week planning exercise, bimonthly schedule template, quick-reference guide summary, commitment form, next steps timeline (March 16 baseline, March 23 launch).

**Step: Commit**

```bash
git commit -m "feat: add math day 2 narration (5 blocks)"
```

---

## Task 5: OV Track Narration — Modules 1-3

**Files:**
- Modify: `index.html` (add narration blocks to ov.modules[0-2].blocks)

Write conversational Spanish narration for OV Modules 1-3:

**M1 — Bienvenida y Contexto**
Blocks: What is EMC, who's involved, your role as tutor, Mi Manifiesto activity, empathy map exercise, bias reflection. Reference the Guía del Tutor sections on adolescent development and common myths.

**M2 — Alfabetización en IA**
Blocks: What is AI / Claude, capabilities vs limitations, 4 myths, responsible use, Pause-Verify-Consult alert protocol. Reference the guide's AI literacy section (pp. 16-18).

**M3 — El Programa**
Blocks: 12-session overview, 8 pedagogical steps (autoconocimiento → plan accionable), session structure (90 min each), platform walkthrough, RIASEC test preview, Explorador de Ocupaciones preview.

**Step: Commit**

```bash
git commit -m "feat: add OV modules 1-3 narration"
```

---

## Task 6: OV Track Narration — Modules 4-6

**Files:**
- Modify: `index.html` (add narration blocks to ov.modules[3-5].blocks)

**M4 — Herramientas**
Blocks: Platform deep dive (student registration, account creation), NotebookLM tutorial, digital diary (Google Docs), fichas/worksheets overview, pre-Session 1 checklist.

**M5 — Práctica y Fricción**
Blocks: Simulated session walkthrough, common difficult situations (reluctant student, no projector, director questions, can't print), 12 key facilitation moves with scripts, role-play exercise.

**M6 — Compromiso y Cierre**
Blocks: Support network (WhatsApp, observation visits), evaluation timeline, action plan template, resource directory (Beca 18, Ponte en Carrera, Línea 100), commitment ceremony, next steps.

**Step: Commit**

```bash
git commit -m "feat: add OV modules 4-6 narration"
```

---

## Task 7: Platform Screenshots Integration

**Files:**
- Create: `img/` directory with platform screenshots
- Modify: `index.html` (add screenshot references in narration)

**Step 1:** Save platform screenshots (taken from uDocz) to `img/` folder:
- `img/platform-login.png` — Login screen
- `img/platform-home.png` — Student dashboard
- `img/platform-question.png` — Math question view
- `img/platform-hint.png` — Hint/feedback view
- `img/platform-progress.png` — Progress/profile view

**Step 2:** Add `<figure>` elements in relevant narration blocks (especially Math Bloque 2 and OV M4) showing platform screenshots with captions:

```html
<figure class="platform-screenshot">
  <img src="img/platform-login.png" alt="Pantalla de inicio de sesión" loading="lazy">
  <figcaption>Así se ve la pantalla de inicio — aquí tus estudiantes ingresarán su DNI y contraseña.</figcaption>
</figure>
```

**Step 3: Commit**

```bash
git add img/ index.html
git commit -m "feat: add platform screenshots to narration"
```

---

## Task 8: GitHub Pages Deployment

**Step 1: Create GitHub repo**

```bash
cd C:\Users\cosmo\Downloads\capacitacion-docentes
gh repo create ezequielmolina-lang/capacitacion-docentes --public --source=. --push
```

**Step 2: Enable GitHub Pages**

```bash
gh api repos/ezequielmolina-lang/capacitacion-docentes/pages -X POST -f source.branch=master -f source.path=/
```

**Step 3: Verify deployment**

Navigate to `https://ezequielmolina-lang.github.io/capacitacion-docentes/` and verify all views work.

**Step 4: Add link to Steal Shamelessly Hub**

Update `C:\Users\cosmo\Downloads\knowledge-hub\index.html` to add a link to the training app (in the capacitacion section alongside the bienvenida-docentes and checklist links).

**Step 5: Commit hub update**

```bash
cd C:\Users\cosmo\Downloads\knowledge-hub
git add index.html
git commit -m "feat: add capacitacion-docentes link to hub"
git push
```

---

## Task 9: Final QA and Polish

**Step 1:** Test all 8 modules — verify slides embed correctly
**Step 2:** Test localStorage progress — complete modules, reload, verify checkmarks persist
**Step 3:** Test mobile responsiveness — resize browser to 375px width
**Step 4:** Verify all resource links open correctly
**Step 5:** Check narration reads naturally, no typos
**Step 6:** Final commit and push

```bash
git push
```
