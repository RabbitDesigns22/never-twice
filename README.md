# never-twice

**An agent skill so the same mistake never happens twice.**

`never-twice` is an agent skill for Claude Code (and any agent that reads `SKILL.md` skills). Agents repeat mistakes because every session starts fresh. One session learns that a label was misleading or that a platform has a trap, and the next session falls into it again.

`never-twice` keeps one shared error log. Every session reads the lines for its topic before starting, and every new mistake is written down with the rule that prevents it.

## What it does

| Problem | How never-twice stops it |
|---|---|
| Repeating old mistakes | Reads `ERRORS.md` for the task's topic before starting. Each line is a rule |
| Claims from memory | Every number, ID, price or status is checked at the source, or marked "not verified" |
| Plans that change mid-way | Thinks the whole plan (risks, safest order, obvious trap) before writing one answer |
| "Done" that isn't | No "done" without real evidence: live version, passing tests, data read back |
| Lessons that get lost | Every new mistake becomes one line in the log, with its rule |

## Install

With the [skills CLI](https://skills.sh):

```bash
npx skills add RabbitDesigns22/never-twice
```

Or manually: copy `skills/never-twice/` into `~/.claude/skills/` for all your projects, or into `.claude/skills/` for one project.

To make every session use it, add this line to your `CLAUDE.md`:

```
Before every task and every answer that recommends, states a status or says "done", load the never-twice skill and read ERRORS.md for the topic.
```

## The error log format

```
- YYYY-MM-DD · TOPIC · what happened · root cause · RULE so it never happens again
```

## Works well with

- [`one-pass`](https://github.com/RabbitDesigns22/one-pass): get it right the first time without burning tokens on rework.
- [`one-answer`](https://github.com/RabbitDesigns22/one-answer): one final answer instead of a plan, a correction and another plan.

## Safety

`never-twice` contains no scripts, makes no network calls and needs no permissions. It is plain instructions. Read it before installing: it is under 100 lines.

## Español

**Una skill para que el mismo error nunca pase dos veces.** Los agentes repiten errores porque cada sesión empieza de cero. `never-twice` guarda un registro de errores compartido (`ERRORS.md`). Antes de empezar, cada sesión lee los errores de su tema. Antes de afirmar algo, lo comprueba. Piensa el plan completo y da una sola respuesta. No dice "listo" sin la prueba real. Y cada error nuevo se anota con la regla que lo evita.

Instalar: `npx skills add RabbitDesigns22/never-twice`

## License

MIT. Made by [Rabbit Designs](https://github.com/RabbitDesigns22).
