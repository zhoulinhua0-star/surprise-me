# surprise-me

**Max visual acuity mode** — a cross-agent skill that makes coding agents (Claude Code, Codex, and anything else that reads `SKILL.md`) produce visual work meant to blow you away instead of serving the default style.

Asking a model to "be creative" changes the wording, not the concept — it picks the same favourite every time. This skill swaps vibes for mechanics:

1. **Dice-rolled direction** — the agent writes 6 fundamentally different directions, then a real shell random roll (`$RANDOM`) picks one.
2. **Written contract** — concept, palette, type pairing, 3+ advanced techniques, hero moment, and bans, locked in a file.
3. **Real assets** — generated/sourced images and motion, not CSS-gradient placeholders.
4. **3+ visual critique passes** — render → screenshot → audit against the contract → fix. Nothing is shown before pass 3.

See [`SKILL.md`](SKILL.md) for the full workflow.

## Install

Clone once, then symlink into each agent's skills folder:

```bash
git clone git@github.com:zhoulinhua0-star/surprise-me.git ~/Developer/surprise-me

# Claude Code
ln -s ~/Developer/surprise-me ~/.claude/skills/surprise-me

# Codex
ln -s ~/Developer/surprise-me ~/.codex/skills/surprise-me

# Other agents that read ~/.agents/skills
ln -s ~/Developer/surprise-me ~/.agents/skills/surprise-me
```

Restart the agent so it picks up the new skill. `git pull` updates it everywhere.

## Use

```
/surprise-me
/surprise-me a landing page for my CLI tool
surprise me with a pitch deck for this project
```

Works best when the agent can take screenshots (Playwright, a headless browser, or a browser tool) and has access to an image-generation tool.

## Credits

Based on the "surprise-me" skill shown by Jay E (RoboNuggets), modeled on his "25 websites with Fable" prompt, and on the [impeccable.style research](https://impeccable.style/research).

## License

MIT
