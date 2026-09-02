# AGENTS.md – Fullstack Application Agent Guidelines (Solo Dev Kit)

This repository is a professional **Fullstack Web Application** development template and cognitive environment optimized for **seamless collaboration between a solo developer and an AI coding agent**.

---

## 🎯 Core Operating Principles for the Agent

1. **Single Source of Truth**:
   - All persistent project data, architecture, product requirements, styling tokens, and status reside in `.agents/blueprint/`.
   - Never make assumptions about features or requirements without checking `.agents/blueprint/PRD.md`.
   - All UI components, buttons, and colors must strictly adhere to `.agents/blueprint/STYLE_GUIDE.md`.
2. **Engineering Standards**:
   - Always follow `.agents/rules/fullstack-dev.md`.
   - Clean, modular architecture with clear separation of concerns (frontend, backend, data layer).
   - Security-first mindset: no secrets in code, validated inputs, proper auth flows.
   - Accessible, responsive, and performant UI (Core Web Vitals compliant).
3. **Context and Token Management**:
   - Keep sessions focused and compact.
   - When the developer ends the session, execute `/save` (`app-memory`).
   - When starting a fresh session, execute `/resume` (`app-memory`) and read only the 2–4 key files specified in `SESSION_STATE.md`.

---

## ⚡ Slash Commands & Skills Mapping

The agent must activate the corresponding skill (`.agents/skills/<skill-name>/SKILL.md`) when the user invokes these commands or requests the corresponding task:

| Command | Skill | Purpose |
| :--- | :--- | :--- |
| `/init` | `app-init` | Initialize new app: *Grill-Me* interview, PRD & blueprint creation, project scaffold |
| `/onboard`, `/audit` | `app-onboard` | Audit and reverse-engineer existing codebase, build blueprint |
| `/review`, `/optimize` | `app-review` | Code quality assurance: performance, security, a11y, SEO, architecture audit |
| `/test` | `app-test` | Automated browser testing: page load, navigation, forms, console errors, responsive |
| `/debug`, `/fix` | `app-debug` | Systematic diagnostics: root cause analysis, fix proposal, `KNOWN_BUGS.md` logging |
| `/save`, `/checkpoint` | `app-memory` | Session end: summarize state, define next task, save handoff context |
| `/resume`, `/start-session` | `app-memory` | Session start: read state and deliver a concise 3-sentence kick-off debrief |
| `/build`, `/deploy` | `app-deploy` | Production build, deployment packaging (Vercel, Netlify, Docker, GitHub Pages) |

---

## 🔄 The Solo Developer Loop

```mermaid
graph TD
    A["🌅 Start Session: /resume"] --> B["🔨 Feature Development & Coding"]
    B --> C["🧪 Verification: /test"]
    C -- Bugs detected --> D["🐛 Diagnostics & Fix: /debug"]
    D --> B
    C -- Clean pass --> E["🔍 Quality & Security Review: /review"]
    E --> F["🌆 End Session: /save"]
    F --> G["🚀 Production Deployment: /build"]
```
