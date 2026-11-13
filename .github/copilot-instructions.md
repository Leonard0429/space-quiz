# Copilot instructions

## Project overview

This repository is a dependency-free, single-page space exploration quiz. The entire app lives in `index.html`, which contains the semantic HTML structure, all CSS, and the vanilla JavaScript quiz state and interaction logic.

The page has two main UI states:

- The quiz view renders one question at a time from the `questions` array, updates the progress bar and score, and applies answer feedback classes for correct and incorrect selections.
- The results view is hidden until the final question is answered, then displays the score, an emoji reaction, contextual copy, and a restart action.

The visual system is implemented with CSS custom properties, layered gradients, stars, a subtle hex grid, responsive sizing, and animated feedback. The app is designed to open directly as a local file and does not require a server or external assets.

## Build, test, and lint

There is no package manager, build step, test suite, or lint configuration in this repository.

To run the app, open `index.html` directly in a browser. The integrated browser can use:

```text
file:///C:/Republic%20Polytechnic/Y2S2/C334%20Agentic%20AI/space-quiz/index.html
```

For focused manual validation, verify the first question, a correct answer, an incorrect answer, progression through all 10 questions, the final results state, and the restart button. There is no single-test command because no automated tests are configured.

## Implementation conventions

- Keep the app self-contained in `index.html`; do not add frameworks, build tooling, or runtime dependencies unless the project requirements explicitly change.
- Add or edit quiz content in the `questions` array. Each item uses `category`, `question`, `answers`, and a zero-based `correct` answer index.
- Keep quiz state in the existing `current`, `score`, and `answered` variables. Use `renderQuestion`, `selectAnswer`, and `showResults` for the established state transitions rather than duplicating flow logic.
- Use the existing DOM element references and CSS classes (`correct`, `wrong`, `good`, `bad`, `pop`) for feedback and animation behavior.
- Preserve the semantic structure and accessible behavior: use real buttons for interactions, keep answer feedback in the `aria-live` element, retain visible focus/hover affordances, and respect `prefers-reduced-motion`.
- Reuse the CSS custom properties in `:root` for colors and shadows. Keep new visual effects subtle enough that question text and answer controls remain the visual priority.
- Preserve responsive behavior for narrow screens. The main content is intentionally centered in a narrow column, with a mobile adjustment in the existing media query.
- The mission-control header includes the semantic `h1`, a decorative kicker, and an `ONLINE` status label. Keep the title text as the heading and use `aria-hidden` only for decorative text.
