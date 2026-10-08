:root {
  --bg: #faf7f4;
  --panel: #f1e9e5;
  --card: #fffdfb;
  --surface: #f7f1ee;
  --fg: #2a2523;
  --muted: #6b625d;
  --accent: #7b2d26;
  --accent-strong: #5f221d;
  --border: #d8cfc9;
  --shadow: rgba(42, 37, 35, 0.08);
}

:root[data-theme="dark"] {
  --bg: #1c1918;
  --panel: #2a2523;
  --card: #241f1d;
  --surface: #2f2927;
  --fg: #ece6e2;
  --muted: #a39a95;
  --accent: #e39a8f;
  --accent-strong: #f0b3a6;
  --border: #453d39;
  --shadow: rgba(0, 0, 0, 0.25);
}

* {
  box-sizing: border-box;
}

html {
  scroll-behavior: smooth;
}

body {
  margin: 0;
  background: var(--bg);
  color: var(--fg);
  font: 17px/1.6 Georgia, "Times New Roman", serif;
}

button,
textarea {
  font: inherit;
}

img {
  max-width: 100%;
}

.skip-link {
  position: absolute;
  left: 1rem;
  top: -3rem;
  z-index: 20;
  background: var(--accent);
  color: #fff;
  padding: 0.75rem 1rem;
  border-radius: 0.5rem;
  text-decoration: none;
  transition: top 0.2s ease;
}

.skip-link:focus {
  top: 1rem;
}

.container {
  width: min(720px, calc(100% - 2rem));
  margin: 0 auto;
}

.site-header {
  border-bottom: 1px solid var(--border);
  background: rgba(255, 255, 255, 0.02);
  backdrop-filter: blur(4px);
}

.header-inner {
  display: flex;
  align-items: center;
  justify-content: space-between;
  gap: 1rem;
  padding: 1.1rem 0 0.9rem;
}

.title-wrap {
  flex: 1;
}

.eyebrow,
.section-kicker,
.prompt-label,
.idea-label,
.reflection-label,
.step-index {
  margin: 0;
  font: 600 0.75rem/1.2 system-ui, sans-serif;
  letter-spacing: 0.08em;
  text-transform: uppercase;
  color: var(--muted);
}

h1 {
  margin: 0.2rem 0 0.15rem;
  font-size: clamp(2rem, 3vw, 2.5rem);
  line-height: 1.15;
  color: var(--accent);
}

.subtitle {
  margin: 0;
  color: var(--accent);
  font-style: italic;
  font-size: 1.15rem;
}

.theme-toggle,
.ghost-button,
.idea-toggle,
.chapter-button,
.modal-close {
  border-radius: 999px;
  border: 1px solid var(--border);
  background: var(--card);
  color: var(--accent);
  cursor: pointer;
  transition: transform 0.15s ease, border-color 0.15s ease, background 0.15s ease;
}

.theme-toggle:hover,
.ghost-button:hover,
.idea-toggle:hover,
.chapter-button:hover,
.modal-close:hover {
  transform: translateY(-1px);
}

.theme-toggle {
  display: inline-flex;
  align-items: center;
  gap: 0.5rem;
  padding: 0.6rem 1rem;
  font: 600 0.9rem system-ui, sans-serif;
}

.page-shell {
  padding: 1.25rem 0 3rem;
}

.panel,
.card {
  background: var(--panel);
  border: 1px solid var(--border);
  border-radius: 1rem;
  box-shadow: 0 8px 18px var(--shadow);
}

.intro {
  padding: 1.2rem 1.2rem 1rem;
}

.intro h2,
.notes-header h2 {
  margin: 0.2rem 0 0;
  color: var(--accent);
  font-size: clamp(1.5rem, 2vw, 1.8rem);
}

.intro p:last-child {
  margin-bottom: 0;
}

.chapter-nav {
  display: flex;
  gap: 0.5rem;
  overflow-x: auto;
  padding: 1rem 0 0.25rem;
  scrollbar-width: thin;
}

.chapter-button {
  flex: none;
  min-width: 2.4rem;
  height: 2.4rem;
  padding: 0 0.8rem;
  font: 600 0.9rem system-ui, sans-serif;
}

.chapter-button.is-active {
  background: var(--accent);
  color: #fff;
  border-color: var(--accent);
}

.content-stack {
  display: grid;
  gap: 1rem;
  margin-top: 1rem;
}

.step {
  padding: 1.1rem 1.1rem 1.2rem;
}

.step-header {
  display: flex;
  align-items: baseline;
  gap: 0.7rem;
  margin-bottom: 0.8rem;
}

.step-title {
  margin: 0;
  color: var(--accent);
  font-size: clamp(1.2rem, 2vw, 1.5rem);
}

.step-body {
  display: grid;
  gap: 1rem;
}

.prompt-block,
.idea-content,
.reflection-block {
  background: var(--surface);
  border: 1px solid var(--border);
  border-radius: 0.9rem;
  padding: 0.8rem 0.9rem;
}

.prompt-text,
.idea-text,
.reflection-text {
  margin: 0.4rem 0 0;
  color: var(--fg);
}

.idea-toggle {
  display: inline-block;
  padding: 0.7rem 1.1rem;
  font: 600 0.9rem system-ui, sans-serif;
}

.idea-content[hidden] {
  display: none;
}

.notes-panel {
  margin-top: 1.2rem;
  padding: 1rem 1rem 1.1rem;
}

.notes-header {
  display: flex;
  align-items: center;
  justify-content: space-between;
  gap: 1rem;
  margin-bottom: 0.6rem;
}

.ghost-button {
  padding: 0.4rem 0.8rem;
  font: 600 0.8rem system-ui, sans-serif;
}

textarea {
  width: 100%;
  min-height: 120px;
  resize: vertical;
  border: 1px solid var(--border);
  border-radius: 0.75rem;
  background: var(--bg);
  color: var(--fg);
  padding: 0.8rem 0.9rem;
}

textarea:focus,
button:focus,
img:focus,
a:focus {
  outline: 2px solid var(--accent);
  outline-offset: 2px;
}

.modal {
  position: fixed;
  inset: 0;
  display: none;
  place-items: center;
  background: rgba(0, 0, 0, 0.92);
  z-index: 30;
  padding: 1rem;
}

.modal.is-open {
  display: grid;
}

.modal img {
  max-width: min(90vw, 1100px);
  max-height: 90vh;
  object-fit: contain;
  border-radius: 0.8rem;
  box-shadow: 0 14px 30px rgba(0, 0, 0, 0.35);
}

.modal-close {
  position: absolute;
  top: 1rem;
  right: 1rem;
  width: 2.8rem;
  height: 2.8rem;
  display: grid;
  place-items: center;
  background: rgba(255, 255, 255, 0.1);
  color: #fff;
  border-color: rgba(255, 255, 255, 0.2);
  font-size: 1.7rem;
}

.sr-only {
  position: absolute;
  width: 1px;
  height: 1px;
  padding: 0;
  margin: -1px;
  overflow: hidden;
  clip: rect(0, 0, 0, 0);
  white-space: nowrap;
  border: 0;
}

@media (max-width: 560px) {
  h1 {
    font-size: 1.8rem;
  }

  .header-inner {
    align-items: flex-start;
    flex-direction: column;
  }

  .theme-toggle {
    width: 100%;
    justify-content: center;
  }
}

@media (prefers-reduced-motion: reduce) {
  html {
    scroll-behavior: auto;
  }

  *, *::before, *::after {
    animation: none !important;
    transition: none !important;
  }
}
