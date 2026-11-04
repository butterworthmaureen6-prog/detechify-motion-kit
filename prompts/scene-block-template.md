# Scene block template

One block per scene in the brief. A scene is one idea, one place, one light preset.

```
SCENE {{n}}: {{name}}                                  {{start}} to {{end}} s
Spoken idea : {{one sentence of what the voice says here, quoted exactly or paraphrased}}
Beat        : {{HOOK | SETUP | PROBLEM | MECHANISM | EXAMPLE | REVEAL | PAYOFF ...}}
Set         : {{topic set}}  (kit: topics/{{topic}}.md)
Light       : {{preset from tokens/lights.json}}  accent: {{colour role}}
Objects     : {{hero objects in view, from the topic file}}
Motion      : {{A appears, then B happens, then C changes; timestamped for key moments}}
Camera      : {{recipe name}}: start pose -> end pose, fov, speed
Handoff     : {{how the next scene begins: follow-packet | screen-dive | rise-reveal | light-shift}}
Text        : keywords: {{term at time}}; labels: {{anchor + text + time window}}
Format notes: 16:9 {{...}} | 9:16 {{...}}
```

Rules:
- Each scene's start pose equals the previous scene's end pose when handing off by flow.
- Scenes tile the audio from 0.0 s to the end with no gaps.
- Every stressed word has a visual beat at its start time.
