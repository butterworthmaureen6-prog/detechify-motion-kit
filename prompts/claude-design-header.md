# Header for every Claude Design brief (v0.3 DRAFT)

The audio-to-brief skill puts this at the top of each brief it writes. It can also be pasted by hand.

---

You are making a realistic 3D explainer video for the **de-tech-ify** channel (IT and AI explained simply).

## Reference kit (already imported or linked in this project)
Repo: `{{KIT_REPO}}`

Read in this order before designing anything:
1. `STYLE_BIBLE.md`: the look and the rules
2. `topics/{{TOPIC}}.md`: the environment, objects, colours and camera for this topic
3. `tokens/palette.json` and `tokens/lights.json`: the only colours and light presets to use
4. `components/`: reference code for the studio, camera flow, data streams, racks and the transcript text layer. Reuse and extend it
5. `sets/server-hall.js` and `scenes/server-hall/`: a finished example of a set and a scene
6. `layouts/shorts-9x16.md` or `layouts/youtube-16x9.md`: the format for this video
7. `motion/camera.md` and `motion/transitions.md`: camera and handoff recipes
8. `prompts/transcript-format.md`: how the words, keywords and labels in this brief work

If a file above cannot be read, use the condensed rules in the DIRECTION and RULES blocks below and say which file was missing.

## Inputs in this project
- Voiceover audio (the timing master)
- `{{SLUG}}.srt`: word-timed captions
- The cue data in this brief (`transcript.json` block): words, events, keywords, labels

## RULES
- Realistic 3D look: dark glossy studio, real-looking hardware, data as light. Orange accent, cyan flow.
- The environment follows the topic (see `topics/`). Do not reuse the server hall for every video.
- On-screen text = captions + keyword cards + 3D labels, all from the cue data. Never show the whole transcript.
- Every spoken sentence gets a literal visual. A reaction lands up to 0.1 s before the word it illustrates.
- Hold the camera most of the time. Move in short ease-out bursts. Hand off between shots by flow (follow, dive, rise), not wipes.
- No clip-art, stock icons, cartoon characters or gradient-mesh backgrounds.
- No real IPs, hostnames, credentials or client data on screen. Use obviously fake values.
- Visual only. No music or sound effects.
- Everything is timed in seconds from the audio.
- If something the brief needs is missing from the kit, say what is missing. Do not invent it silently.
