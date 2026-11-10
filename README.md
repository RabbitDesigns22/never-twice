# never-twice

**An agent skill so the same mistake never happens twice.**

`never-twice` is an agent skill for Claude Code (and any agent that reads `SKILL.md` skills). Agents repeat mistakes because every session starts fresh. One session learns that a label was misleading or that a platform has a trap, and the next session falls into it again.

`never-twice` keeps one shared error log. Every session reads the lines for its topic before starting, and every new mistake is written down with the rule that prevents it.

## See the difference

> **You:** You scheduled the post on the wrong date again.

**Without the skill:** the agent apologizes, fixes it, and next week another session makes the same mistake.

**With the skill:** the mistake goes into a shared error log under its topic, with the rule that prevents it. Every session reads that topic before the same kind of task.

**Skip it if** you run one short session and never come back to the project.

**Status:** in daily use in the author's own setup. Plain instructions, no scripts, no network calls. MIT. Issues and suggestions welcome.

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

## More skills from the same setup

These come from one real workflow: a small agency run with 15+ Claude Code sessions in parallel. Each skill fixes one problem that kept happening there.

| Skill | What it fixes |
|---|---|
| [one-pass](https://github.com/RabbitDesigns22/one-pass) | get it right the first time; stop paying tokens for rework |
| [hora-exacta](https://github.com/RabbitDesigns22/hora-exacta) | real date and time in every message, so nothing lands on the wrong day |
| [hands-on](https://github.com/RabbitDesigns22/hands-on) | the agent does what it can and only asks you for codes, keys and payments |
| [easy-for-them](https://github.com/RabbitDesigns22/easy-for-them) | steps people actually follow: direct link, one action per line |
| [one-answer](https://github.com/RabbitDesigns22/one-answer) | one thought-through answer instead of plan, fix, new plan |
| [report-now](https://github.com/RabbitDesigns22/report-now) | status checked live this minute, stamped with the time |
| [sort-me-out](https://github.com/RabbitDesigns22/sort-me-out) | one ordered list of what is urgent, waiting and forgotten |
| [in-the-loop](https://github.com/RabbitDesigns22/in-the-loop) | a live board so parallel sessions know what the others changed |
| [study-first](https://github.com/RabbitDesigns22/study-first) | reads everything in full and answers point by point, no invented details |
| [session-watchdog](https://github.com/RabbitDesigns22/session-watchdog) | wakes the sessions that got stuck mid-task, leaves the rest alone |
| [skill-harvest](https://github.com/RabbitDesigns22/skill-harvest) | reads your sessions and finds the skills you are missing |
| [small-budget-ads](https://github.com/RabbitDesigns22/small-budget-ads) | Meta Ads rules for 1-5 USD a day ad sets |
| [whatsapp-closer](https://github.com/RabbitDesigns22/whatsapp-closer) | evidence-ranked rules for a WhatsApp sales assistant that closes |
| [whatsapp-number-onboarding](https://github.com/RabbitDesigns22/whatsapp-number-onboarding) | connect a number to the WhatsApp Cloud API in the safe order |
| [proposal-pdf](https://github.com/RabbitDesigns22/proposal-pdf) | short PDF proposals with every price checked against its source |
| [published-vs-planned](https://github.com/RabbitDesigns22/published-vs-planned) | says "published" only for what it saw live on the public page, Facebook and Instagram checked apart |
| [source-every-fact](https://github.com/RabbitDesigns22/source-every-fact) | every price, phone and name on a post traced to its source, nothing added |
| [only-what-was-asked](https://github.com/RabbitDesigns22/only-what-was-asked) | "pause only Google Ads" pauses only Google Ads, and proves the rest did not move |
| [model-per-chat](https://github.com/RabbitDesigns22/model-per-chat) | the right model for each chat: top model where mistakes cost money, cheap or none where it only runs often |

If one of them saved you a redo, a star helps other people find it.

## License

MIT. Made by [Rabbit Designs](https://github.com/RabbitDesigns22).
