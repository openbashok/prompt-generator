# Contributing

[Español abajo ⬇](#contribuir-es)

Thanks for taking the time. This tool is one HTML file with vanilla JS — there is no build, no framework, no transpiler. That's on purpose.

## Ground rules

- **No build step.** If your change needs npm, webpack, or a transpiler, it's out of scope. Inline `<style>` and `<script>` in `index.html`.
- **No external runtime dependencies.** Google Fonts is the only allowed exception (already in use). No CDN-loaded JS libraries.
- **No telemetry, no analytics, no trackers.** Period.
- **Both languages.** Every user-facing string lives under `I18N.en` *and* `I18N.es` in the script section. If you add UI text, add both. Spanish defaults to **Rioplatense**.
- **Pentester first.** When in doubt about scope or default, ask: *would this make a pentester's life easier when writing a finding or running an engagement?* If yes, ship it. If it's generic LLM-tool stuff, think twice.

## What's welcome

- New **presets** (in both `en` and `es` blocks). Aim for ones that solve a recurring real-world task, not toy examples.
- New **NO·rules** that are genuinely universal across pentest workflows.
- New **`SKILL.md` validation** checks aligned with the [agentskills.io](https://agentskills.io) standard.
- **Bug fixes**, especially around `localStorage` migration, token estimation, output rendering, and the AI backend calls.
- **Accessibility** improvements (keyboard nav, contrast, screen-reader labels).
- **Translation fixes** — the ES strings should sound natural to a Rioplatense speaker, not translated-from-English.

## What's probably out of scope

- A backend. The point is no backend.
- A framework (React/Vue/etc.).
- Light theme (the dark theme is part of the identity).
- New providers beyond Anthropic / OpenAI, unless they're widely used by pentesters.
- Removing the "from pentesters, to pentesters" framing — the defaults are intentional.

## How to contribute

1. Open an issue first if the change is non-trivial. Saves both sides time.
2. Fork → branch off `main` → small focused PR.
3. Test in at least one current Chromium-based and one Firefox-based browser.
4. Test **both EN and ES**.
5. Keep the diff minimal. No drive-by refactors.

## Style

- Vanilla JS, no jQuery, no helpers from npm.
- 2-space indentation.
- Constants in `UPPER_SNAKE`, functions in `camelCase`, CSS variables in `--kebab-case`.
- Inline comments only when the *why* is non-obvious. The *what* should be readable from the code.

## License

By contributing, you agree your changes are released under the [MIT License](LICENSE).

---

<a name="contribuir-es"></a>
## Contribuir (ES)

Gracias por el tiempo. Esta tool es un archivo HTML con JS vanilla — sin build, sin framework, sin transpiler. Es a propósito.

### Reglas base

- **Sin build step.** Si tu cambio necesita npm, webpack o transpiler, está fuera de scope. Todo `<style>` y `<script>` inline en `index.html`.
- **Sin dependencias externas en runtime.** Google Fonts es la única excepción (ya en uso). Nada de librerías JS por CDN.
- **Sin telemetría, sin analytics, sin trackers.** Punto.
- **Ambos idiomas.** Cada string user-facing vive bajo `I18N.en` *y* `I18N.es`. Si agregás texto UI, agregá los dos. Español default es **rioplatense**.
- **Pentester primero.** Si dudás del scope o un default, preguntate: *¿esto le hace la vida más fácil a un pentester redactando un finding o corriendo un engagement?* Si sí, va. Si es genérico de tools LLM, pensalo dos veces.

### Lo que es bienvenido

- Nuevos **presets** (en bloques `en` y `es`). Apuntá a tareas recurrentes reales, no ejemplos de juguete.
- Nuevas **reglas NO** que sean genuinamente universales para workflows de pentest.
- Nuevos checks de validación para **`SKILL.md`** alineados con el estándar [agentskills.io](https://agentskills.io).
- **Bug fixes**, especialmente en `localStorage`, estimación de tokens, render del output, y las llamadas al backend IA.
- Mejoras de **accesibilidad** (nav por teclado, contraste, labels para screen readers).
- **Fixes de traducción** — los strings ES tienen que sonar natural a un rioplatense, no traducidos-del-inglés.

### Lo que probablemente está fuera de scope

- Un backend. El punto es no tener backend.
- Un framework (React/Vue/etc).
- Tema light (el dark theme es parte de la identidad).
- Providers nuevos más allá de Anthropic / OpenAI, salvo que los use mucha gente de pentest.
- Sacarle el framing "de pentesters, para pentesters" — los defaults son intencionales.

### Cómo contribuir

1. Abrí un issue primero si el cambio no es trivial. Ahorra tiempo a las dos partes.
2. Fork → branch desde `main` → PR chico y focalizado.
3. Probá en al menos un navegador Chromium y uno Firefox.
4. Probá **EN y ES**.
5. Mantené el diff mínimo. Sin refactors al pasar.

### Estilo

- JS vanilla, sin jQuery, sin helpers de npm.
- Indentación 2 espacios.
- Constantes en `UPPER_SNAKE`, funciones en `camelCase`, variables CSS en `--kebab-case`.
- Comentarios inline solo cuando el *por qué* no es obvio. El *qué* tiene que leerse del código.

### Licencia

Al contribuir, tus cambios se publican bajo la [Licencia MIT](LICENSE).
