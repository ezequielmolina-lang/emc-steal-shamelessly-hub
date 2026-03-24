# Capacitacion Docentes — Interactive Training App

**Date:** 2026-03-24
**Status:** Approved
**Repo:** `ezequielmolina-lang/capacitacion-docentes`
**URL:** `https://ezequielmolina-lang.github.io/capacitacion-docentes/`

## Purpose

Self-paced training app for teachers who missed the in-person math and orientacion vocacional training sessions. Embeds the actual training slides with written narration (conversational Spanish, tuteo) so teachers can go through the full training independently.

## User Flow

```
Landing Page (pick track)
    ├── Matematicas
    │   ├── Dia 1 (Bloques 1-5): AI literacy, platform, registration, curriculum, dashboard
    │   └── Dia 2 (Bloques 6-10): experimental design, classroom mgmt, simulation, accompaniment, action plan
    └── Orientacion Vocacional
        ├── Modulo 1
        ├── Modulo 2
        ├── Modulo 3
        ├── Modulo 4
        ├── Modulo 5
        └── Modulo 6
```

## Content Sources

### Matematicas Track

| Module | Slides Embed ID | Narration Source |
|--------|----------------|-----------------|
| Dia 1 | `1V_ID56Czrnv0XfMCQTO8rutsnJ4Fb4-ePGe7GYoDuOU` | Guia Docente Matematicas |
| Dia 2 | `1eYwrDWsaJF6v7fXVCQiCpf5uCspyXltIYHyvxYPw9lU` | Guia Docente Matematicas |

- **Guia Docente PDF:** `12Q5zUjofNHHfONZT2nSSQVOGH8M2zuan`
- **Math folder:** `https://drive.google.com/drive/folders/1kfWgFFFpGl9LDKlUhREi9cBjERI2BJm3`
- **Slides folder:** `https://drive.google.com/drive/folders/1h_I1p-dcWMnMM8__eAFuV_vjkNkMEkO-`

### Orientacion Vocacional Track

| Module | Slides Embed ID | Narration Source |
|--------|----------------|-----------------|
| M1 | `11h97scJhZ9gOJETm4xH71MaB45bAeq0v` | Guia del Tutor OV |
| M2 | `1FHOp5UZ-1tZ9663v8TMuXzSOpFy-tuYE` | Guia del Tutor OV |
| M3 | `1NdvFA8KHBqC7ylinv88MNBgeKpmY3D5o` | Guia del Tutor OV |
| M4 | `1tQiMK_JG-vdaSf2E3Ra2VTkBMHTdsEyG` | Guia del Tutor OV |
| M5 | `1Oj1zJ6pVGW3jySS5NleCfURf0Pmw_bKQ` | Guia del Tutor OV |
| M6 | `1YGWLaQVS-GoGWO1jYincqIpS_JVklndD` | Guia del Tutor OV |

- **Guia del Tutor OV PDF:** `1_KfUBZ2gCql4iFDlv1UqFKSyBGpBl_GF`
- **OV folder:** `https://drive.google.com/drive/folders/1m_OnilfgQSEJusmA3nz9Xk8-hcq8rsVo`
- **Slides folder:** `https://drive.google.com/drive/folders/1tZWTL0cRKIunBRbaH3bFrK2g34WcW-ir`

## Technical Architecture

- **Stack:** Single HTML file, vanilla CSS/JS (no framework), same as bienvenida-docentes
- **Hosting:** GitHub Pages
- **Views:** All managed by JS state in one page (landing, module list, slideshow view)
- **Slides:** Google Slides embed iframe (full width, ~60vh)
- **Narration:** Scrollable text panel below slides, organized as collapsible block sections
- **Progress:** localStorage — tracks completed modules per track, no login
- **Branding:** Orange gradient, EMC logo, partner badges (same as bienvenida-docentes)

## Narration Format

Each module page:

1. **Embedded slides** — Google Slides iframe with built-in navigation
2. **Narration guide** — Collapsible sections matching slide blocks, conversational tone (tuteo), references specific slide numbers
3. **Recursos section** — Links to guide PDF, slides folder, supplementary docs
4. **"Marcar como completado" button** — Saves to localStorage

### Audio-ready structure

Each narration block section will have a data attribute and container ready for a future `<audio>` element with play/pause controls. No audio in v1.

## Math Training Content (Day 1 & Day 2)

### Day 1 — 5 Blocks

1. **Bloque 1 — Bienvenida, contexto y alfabetizacion en IA** (8:00-9:15): Program overview, AI literacy, myths, hands-on with ChatGPT/MaestroAI
2. **Bloque 2 — Conociendo la plataforma UDocz como estudiante** (9:30-11:00): Platform walkthrough, guided practice, diagnostic questions, Modo Escuela vs Modo Casa
3. **Bloque 3 — Registro de estudiantes y preparacion logistica** (11:15-12:30): Rosters, account creation, password protocol, pre-launch verification
4. **Bloque 4 — Integracion curricular segun carga horaria** (13:30-14:45): 4h vs 6h schools, CNEB mapping, schedule drafting exercise
5. **Bloque 5 — Dashboard del docente** (15:00-16:30): Real-time dashboard, resolution categories, error analysis, simulated data exercise

### Day 2 — 5 Blocks

6. **Bloque 6 — El diseno experimental (Modelo B vs. B')** (8:00-9:15): B' modifications (retrieval practice, predict/reveal/diagnose, planted errors), live demo
7. **Bloque 7 — Gestion del aula durante sesiones de IA** (9:30-11:00): Session start protocol, teacher role during sessions, what NOT to do, common situations
8. **Bloque 8 — Simulacion de sesion completa (MODELADO)** (11:15-12:30): 40-min simulated session, debrief, role reversal
9. **Bloque 9 — Acompanamiento, comunicacion y evaluaciones** (13:30-14:45): WhatsApp support, observation visits, evaluation calendar
10. **Bloque 10 — Plan de accion individual y cierre** (15:00-17:00): Pre-launch checklist, 4-week plan, Q&A, certificate

## Design Decisions

- **No login required** — teachers bookmark and continue; localStorage tracks progress
- **Google Slides iframe** — avoids duplicating slide content; teachers see the real presentations
- **Collapsible narration** — teachers can expand only the block they're on, reducing overwhelm
- **Slide number references** — narration says "En la diapositiva 3..." so teachers can sync manually
- **Audio-ready** — HTML structure supports adding audio per block later without restructuring
