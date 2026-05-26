# OpenBash · Prompt Generator

> **De pentesters, para pentesters.**
> Generador estructurado de **prompts**, archivos **`CLAUDE.md`** de proyecto y **`SKILL.md`** de agente — armado para trabajo de offensive security.

[![License: MIT](https://img.shields.io/badge/License-MIT-blue.svg)](LICENSE)
[![Made by OpenBash](https://img.shields.io/badge/hecho%20por-openbash.com-ff2a78)](https://openbash.com)
[![Sin backend](https://img.shields.io/badge/100%25-client--side-00e5ff)](#privacidad)
[![EN / ES](https://img.shields.io/badge/i18n-EN%20%2F%20ES-a855f7)](README.md)

**Español** · [English](README.md)

---

## Qué es esto

Una herramienta single-page que convierte instrucciones sueltas tipo "hacé X, pero nunca Y, y respondé con esta forma" en artifacts estructurados que los LLMs realmente siguen:

- **`PROMPT`** — instrucción one-shot para una tarea. Lo pegás en una conversación.
- **`CLAUDE.md`** — archivo de contexto de proyecto que [Claude Code](https://claude.com/claude-code) carga automático desde la raíz del repo.
- **`SKILL.md`** — [skill de agente](https://agentskills.io) reusable con YAML frontmatter, cargado dinámicamente cuando matchean los triggers.

Faders para **creatividad**, **rigor**, **verbosidad** y **tono**. **Reglas NO** duras que se inyectan como meta-instrucciones y sobreviven cualquier refinamiento. Preview en vivo, contador de tokens, validación para `SKILL.md`, y presets curados para pentesters (redactor de findings, evaluador CVSS, validador de evidencia, categorizador OWASP, workspace de engagement, redacción de reportes y más).

### Por qué pentesters

Porque redactar un finding que aguante una review del cliente no es una tarea creativa — es estructurada, con reglas duras ("nunca parafrasear evidencia", "nunca exagerar severidad", "nunca mezclar remediación con descripción"). Los LLMs son útiles para esto, pero solo si están restringidos. Esta herramienta arma esas restricciones dentro del prompt.

Funciona para cualquier tarea de prompting estructurado, pero los defaults, presets y reglas se inclinan hacia **offensive security y redacción de reportes**.

## Features

- **3 modos**: Prompt · `CLAUDE.md` · `SKILL.md` — cada uno con sus propias secciones, presets, placeholders y reglas de validación.
- **EN / ES** — UI traducida completa. Español por default rioplatense.
- **Faders**: creatividad (0–1), rigor (0–1), verbosidad (conciso → exhaustivo), tono (casual → formal). Los faders alteran el output renderizado *y* la temperature de la API cuando el panel IA está activo.
- **Reglas NO** — reglas duras universales (no inventar, no inferir más allá del input, sin filler, sin emojis, sin markdown si no se pidió, sin language drift…) más reglas custom por preset.
- **Presets** curados para workflows de pentest: `pentest-finding`, `code-review`, `extractor`, `pentest-engagement`, `security-tool-repo`, `report-writing`, `pentest-finding-writer`, `severity-assessor`, `evidence-validator`, `owasp-categorizer`, …
- **Preview en vivo** + estimación de tokens + validación estructural (`SKILL.md` chequea el YAML frontmatter y avisa sobre descripciones débiles, triggers faltantes, archivos sobredimensionados).
- **Backend IA opcional** — bring your own key para Anthropic Claude o OpenAI GPT. Acciones `MEJORAR` / `TEST RUN` / `CRITICAR` usan tu output actual + faders.
- **100% client-side** — sin backend, sin telemetría, sin analytics. El estado vive en `localStorage`. Tu API key nunca sale del navegador salvo para ir al provider.

## Cómo usarlo

**Hosteado:** abrí el sitio de GitHub Pages (activado en este repo).

**Local:** cloneá el repo y abrí `index.html` en cualquier navegador moderno. Listo — no hay build, no hay dependencias, no hay nada que instalar.

```bash
git clone https://github.com/openbashok/prompt-generator.git
cd prompt-generator
open index.html        # macOS
xdg-open index.html    # Linux
start index.html       # Windows
```

O servilo con cualquier cosa:

```bash
python3 -m http.server 8000
# después abrí http://localhost:8000
```

## Cómo se usa

1. Elegí un **modo** (Prompt / `CLAUDE.md` / `SKILL.md`).
2. Opcionalmente cargá un **preset** desde el panel izquierdo.
3. Activá las **secciones** que querés en el output.
4. Llená los campos de **contenido** en la columna del medio. El preview se actualiza solo.
5. Ajustá los **faders** al tipo de tarea (creatividad baja + rigor alto para findings; creatividad alta para explainers).
6. Agregá o quitá **reglas NO** — las universales están activas por default; cliqueá los chips para togglear, agregá custom en el input.
7. **COPIAR** o **DESCARGAR** el resultado.
8. *(Opcional)* Abrí el **panel IA** en el header, cargá una key de Anthropic u OpenAI, y usá `MEJORAR` / `TEST RUN` / `CRITICAR` para iterar.

### Ejemplos de output

- **Modo Prompt** → texto plano con secciones `ROL / CONTEXTO / TAREA / INPUT / RESTRICCIONES / FORMATO / REGLAS DURAS`, listo para pegar.
- **Modo `CLAUDE.md`** → droppealo en la raíz de cualquier repo. Claude Code lo lee automático.
- **Modo `SKILL.md`** → guardalo como `skills/<nombre>/SKILL.md`. Incluye el YAML frontmatter (`name`, `description`) requerido por el estándar [agentskills.io](https://agentskills.io).

## Privacidad

- Todo corre en tu navegador. No hay servidor.
- Las API keys viven solo en `localStorage`. Se mandan **directo** al provider que elijas (Anthropic / OpenAI), nunca a un intermediario.
- Para producción o entornos compartidos, pasá las llamadas IA por un proxy backend en vez de poner keys en el navegador.

## Roadmap

Esto es `v0.5`. En el radar:

- Más presets (pentest mobile, AD/network, cloud, red team ops, threat modeling).
- Skill categorizador CWE, skill redactor de remediación.
- Export a JSON / import de presets entre navegadores.
- Más providers (modelos locales, Ollama).
- Toggle opcional dark/light (hoy solo dark — es feature).

PRs bienvenidos — ver [`CONTRIBUTING.md`](CONTRIBUTING.md).

## Contribuir

¿Encontraste un preset que falta, una regla que debería ser universal, un issue de traducción, o un bug?

- Abrí un issue con un ejemplo concreto.
- O mandá un PR — toda la app es un archivo HTML con JS vanilla, sin build, sin framework, sin transpilación. Fácil de hackear.

Ver [`CONTRIBUTING.md`](CONTRIBUTING.md) para la versión corta.

## Licencia

[MIT](LICENSE) — hacé lo que quieras, solo dejá el notice.

## Sobre OpenBash

[OpenBash](https://openbash.com) construye tooling para equipos de offensive security.
Este proyecto es parte de ese toolbox. Hecho por pentesters, para pentesters.
