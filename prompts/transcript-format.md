# Transcript format (`transcript.json`)

The text layer (`components/transcriptText.js`) reads this. The audio-to-brief skill produces it from the voiceover. Claude Design should build its on-screen text from it, so words on screen always match the audio.

```json
{
  "title": "Cleaning raw data",
  "topic": "data-cleaning",
  "duration": 31.2,
  "events": { "detect": 1.7, "wrong": 6.1, "dups": 10.4, "missing": 14.0, "format": 18.2, "clean": 23.5 },
  "words": [ { "w": "Raw", "s": 0.3, "e": 0.62 }, { "w": "data", "s": 0.66, "e": 0.98 } ],
  "keywords": [ { "at": 0.3, "text": "Raw data", "sub": "messy by default", "dur": 2.4 } ],
  "labels": [ { "anchor": "row-dup", "text": "duplicate row", "tone": "amber", "s": 3.4, "e": 6.6, "pill_at": "edge-right", "side": "r" } ]
}
```

## Fields
| Field | Meaning |
|---|---|
| `words` | Every spoken word with start and end seconds, from the word-timed transcription. Never invented. |
| `events` | Named story moments (seconds). Animations key off these. Pick words that start a new idea ("First", "Now"). |
| `keywords` | Big pop-in cards. At most one per 3 seconds. `at` is the start time of the word being spoken. |
| `labels` | Pills pinned to objects. `anchor` is a semantic name the scene must expose. `tone` is amber, red, cyan, green, orange or violet. |

## Rules for the text layer
- **Captions:** show 2-4 words at a time, break at punctuation, hold until the next group unless there is a pause over 0.6 s. The current word is orange, spoken words white, upcoming words dimmed.
- **Keyword cards:** pop in on the word, stay 2-2.5 s, never over two at once. Use the term or number being explained, never a whole sentence.
- **3D labels:** at most four at once. Pills sit outside the object where possible and are clamped to stay on screen. A thin leader line joins pill to anchor.
- **Never show the whole transcript.** Captions plus a few keywords plus labels is the ceiling.
- Everything is a pure function of time, so any frame can be rendered on demand.
- Safe zones follow `layouts/`. In 9:16, captions sit about 24% up from the bottom.

## Anchors
A scene defines its own anchors (for example `rack:L3` in `sets/server-hall.js`). When a brief uses a label, it names the anchor semantically ("row-dup", "blank-cell", "weak-point") and the scene must provide it. If Claude Design builds a new set, it exposes anchors the same way: `getAnchor(name, outVec3) -> boolean`.

## Making one
- From an SRT: `node tools/srt-to-transcript.mjs voiceover.srt scenes/<slug>/script.json "<title>" <topic>`, then add events, keywords and labels.
- From the skill: it writes the JSON block straight into the brief.
