# Repository Guidelines

## Project Structure & Module Organization
The project is intentionally flat. `index.html` contains the markup, inline styles, and vanilla JS powering the drag-and-drop tutor. Audio cues (`delete.mp3`, `drop.mp3`) and the UI reference image (`form.png`) sit beside it for easy relative imports. When you add media, keep names descriptive (e.g., `delete-warning.mp3`) and update the `<audio>` sources near the top of `index.html` so offline deployments stay self-contained.

## Build, Test, and Development Commands
- `python3 -m http.server 4173`: start a lightweight preview server at `http://localhost:4173`.
- `npx serve . -l 4173`: Node-based alternative that sets stricter MIME headers for audio.
- `npx prettier --write index.html`: optional formatter pass to keep one-file contributions tidy.
Work inside a single browser tab, save, and refresh; no bundler or dependency install is required.

## Coding Style & Naming Conventions
Indent HTML, CSS, and script blocks with two spaces to match the existing layout. Favor semantic container names (`.drop-zone`, `.slot`) and lowercase, hyphenated selectors. JavaScript handles should end in `El` (e.g., `menuButtonEl`) to distinguish them from data. Keep hover interactions in CSS when possible, fall back to JS only for drag logic, and add short comments before non-obvious helper functions.

## Testing Guidelines
Automated tests are not yet configured, so rely on a quick manual checklist every change: verify drag/drop on mouse and touch, ensure delete buttons reveal on hover only, confirm audio cues play without console errors, and resize the viewport to catch wrapping issues inside `.drop-zone`. Record browser/OS combinations in the PR description so regressions can be traced.

## Commit & Pull Request Guidelines
Commits should follow the imperative style seen in `git log` (e.g., `add transparent slot guides`). Keep them small, reference assets you touched, and describe any UX shifts. Pull requests need a short summary, screenshots or GIFs for visual tweaks, links to any related tasks, and a bullet list of manual tests executed. Mention any follow-up work (e.g., refactoring inline CSS) to guide future contributors.

## Security & Configuration Tips
Because classrooms often run this offline, avoid hotlinking fonts or media. Stick to passive audio playback to prevent browser permission prompts, debounce pointer listeners to avoid performance spikes, and sanitize any future user-input handlers before saving text inside dropped tiles.
