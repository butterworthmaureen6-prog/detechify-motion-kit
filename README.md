# detechify-motion-kit

Reference kit for **Claude Design**. It is not a render pipeline. Claude Design reads it to build realistic 3D explainers for the **de-tech-ify** channel (YouTube 16:9 and Shorts 9:16) that look like one channel across every topic.

How it fits together:

```
voiceover audio
   -> Claude skill (audio-to-3d-explainer-prompt)  -> <slug>.srt + <slug>-brief.md
   -> Claude Design (this repo imported) + audio + SRT + brief -> animation
```

The brief names the topic, set, light preset, camera recipes and text cues. This repo holds the details behind those names.

> Status: **v0.3 DRAFT.** One finished set (`server-hall`) and a working text layer prove the look. Other topics have written recipes, not built sets: Claude Design builds them from the recipe.

## The look
Dark glossy studio, realistic hardware, data shown as glowing light, one warm orange accent. Environments change per topic. Words on screen come from the transcript: captions, keyword cards and labels pinned to 3D objects. See `STYLE_BIBLE.md`.

## Map
| Path | What lives there |
|---|---|
| `STYLE_BIBLE.md` | The look as rules |
| `topics/` | One recipe per topic: data-cleaning, networking, cybersecurity, ai, cloud-infra. Environment, objects, colours, camera, text, avoid-list |
| `prompts/` | `claude-design-header.md`, `scene-block-template.md`, `transcript-format.md` (used by the skill when it writes a brief) |
| `tokens/` | `palette.json`, `lights.json` (light presets). Read by the code |
| `components/` | Reference code: `studio`, `rack`, `dataStreams`, `cameraFlow`, `host`, `transcriptText` |
| `sets/` | Finished environments as modules. `server-hall.js` |
| `scenes/` | Runnable scenes: `server-hall/` (with a sample `script.json`) |
| `motion/`, `layouts/` | Camera and transition recipes, 9:16 and 16:9 composition |
| `models/`, `hdri/`, `textures/`, `props/`, `ui/screenshots/` | CC0 or own assets and scrubbed UI screenshots |
| `references/notes/` | Our own study notes. No third-party frames |
| `tools/` | `build-scene.mjs`, `render-still.cjs`, `srt-to-transcript.mjs` |
| `LICENSES.md` | Source and licence for every asset |

## Rules for what goes in
1. Only assets we made, or CC0 / clearly licensed. Log each in `LICENSES.md`.
2. No other creators' frames, models, scripts or logos.
3. Scrub screenshots: no real IPs, hostnames, tokens or client data.
4. Models are GLB under 5 MB. Procedural geometry first.
5. A new topic gets a `topics/<name>.md` before any code.

## Try the reference scene
```bash
npm install
npm run build:scene -- scenes/server-hall      # dist/server-hall.html
```
Open it in a browser. Buttons switch 16:9 / 9:16 and toggle the text layer.
