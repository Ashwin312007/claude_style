# claude_style

A portable instruction file (`SKILL.md`) that shapes how non-Claude language models respond. It asks them to follow a Claude-like style: answer first, match length to the request, use prose by default, flag uncertainty honestly, and handle pushback on the merits.

## What this is

`SKILL.md` is plain-text guidance. You load it into a model's system prompt or into a skill-aware harness, and the model uses it as its default working style. It works with any model that accepts instructions, including Gemini models in Antigravity.

## What this is not

- **Not a change to the model.** The underlying model still reasons with its own weights. The file shapes tone, structure, and habits. It does not replicate Claude's judgment.
- **Not affiliated with Anthropic.** "Claude" is a trademark of Anthropic. This project is an independent set of instructions. It does not reproduce Anthropic's system prompts.

## Contents

| File | Purpose |
| --- | --- |
| `SKILL.md` | The instructions: core approach, formatting, honesty, task habits, safety, self-check, and examples |
| `LICENSE` | MIT License |

## Usage

### As a system prompt

Copy everything below the YAML frontmatter (the `---` block at the top) into your model's system instruction or base prompt. Keep the frontmatter out, since it is metadata for skill loaders.

### As a skill

Place this folder in any directory your harness scans for skills, keeping `SKILL.md` at the folder root. The `description` field in the frontmatter tells the harness when to load the skill.

### With Gemini in Antigravity

Add the body of `SKILL.md` to the agent's system instruction or base prompt. If Antigravity supports loadable instruction files, place `SKILL.md` where it reads them.

## Testing

Pick 10 or so prompts you know well and run each one twice: once with the skill and once without. Compare:

- Whether the answer leads with the direct response
- Length, and whether there is padding or repeated summaries
- Formatting: prose versus unnecessary bullets, headers, and bold
- Whether the model invents facts or overclaims abilities
- How it responds to pushback on a correct answer, and to pushback on a wrong one

Adjust the wording where the model consistently misses a behavior.

## Limitations

- Models drift on long tasks and may not follow every rule under pressure.
- Instructions reduce confident errors but do not eliminate them. Review anything important.
- Some behaviors, such as calibration and judgment on hard questions, depend on the model itself and cannot be fully specified in text.

## Contributing

Issues and pull requests are welcome, especially test cases showing where a model fails to follow a rule.

## License

Released under the MIT License. See [LICENSE](LICENSE).
