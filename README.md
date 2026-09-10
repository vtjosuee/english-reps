# English Reps

A daily English trainer I built for myself, to get from B1 to a solid B2 — the level almost every IT job advert in Madrid asks for.

It is one self-contained HTML file. No build step, no dependencies, no framework.

## What is in it

| Section | What it does |
|---|---|
| **Today** | The 15-minute session: listen, speak, one grammar entry. Keeps a day streak. |
| **Listen** | Dictation. The page reads a sentence aloud, you type it, and it shows a word-by-word diff of what you missed and what you invented. |
| **Speak** | A prompt, answered **out loud**, then written down (or dictated with the microphone) and corrected. |
| **Write** | Six writing tasks — a support email, a cover message, a hotel request — with corrections and the reason for each one. |
| **Read** | Three texts (a support ticket, an IT job advert, an airport scene) with a glossary and comprehension questions. |
| **Grammar** | 22 confusables: the pairs that are one single thing in Spanish and two different things in English. `another / other / any other`, `say / tell`, present perfect vs past simple, false friends, and so on. |
| **Interview** | Ten interview answers written from my actual CV, with a read-aloud button and a target time for each. |

The interface is in English on purpose. The grammar explanations are in Spanish, because that is where the contrast between the two languages actually lives — explaining *another* vs *other* in English teaches a Spanish speaker nothing.

## Two places it runs, and the difference

**GitHub Pages** — this repository, served as a normal web page.

- Microphone dictation works properly (a real top-level HTTPS page is not sandboxed).
- Progress is stored in `localStorage`, so it is per device: the phone and the laptop keep separate streaks.
- The **Check my English** button in *Write* and *Speak* does **not** work here. It has nothing to ask.

**As a Claude Artifact** — the same file, published on claude.ai.

- **Check my English** works: writing and speaking get corrected, with the reason for every error.
- Progress is stored server-side and follows me between devices.
- Microphone dictation may be blocked by the sandbox.

The code detects which of the two it is running in and turns features on or off accordingly. Nothing breaks either way.

## Changing the content

All the material lives in plain arrays at the top of the `<script>` block in `index.html`:

| Array | Holds |
|---|---|
| `CONFUSABLES` | Grammar entries: rule, Spanish contrast, examples, drills. |
| `DICTATION` | Dictation sentences, tagged `work` / `travel` / `daily` / `job`. |
| `SPEAK` | Speaking prompts. |
| `WRITE` | Writing tasks. |
| `READINGS` | Reading texts with glossary and questions. |
| `INTERVIEW` | Interview questions and answers. |

Add an object to any array and it appears in the page. Nothing else has to be touched.

## Running it locally

Open `index.html` in a browser. That is the whole procedure.

The speech comes from the browser's own `speechSynthesis`, so no audio files are downloaded and nothing external is needed. If nothing is spoken, the device has no English voice installed.

## Licence

Personal project. Take anything that is useful to you.
