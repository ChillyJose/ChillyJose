# Idea Backlog — rules of the loop

*Last revised 2026-09-05*

These rules govern the **Idea Loop** (`loop-idea-backlog`) and any other loop that writes into
this folder. They exist because the backlog is currently ~5x oversupplied while view data is
missing — the bottleneck is measurement, not ideas.

## Files

| File | Purpose |
|---|---|
| `channel-A-finance-ideas.md` | Channel A backlog |
| `channel-B-tech-science-ideas.md` | Channel B backlog |
| `channel-C-history-ideas.md` | Channel C backlog |
| `production-queue.md` | The next 20 Shorts, weighted by channel performance |
| `archive/` | Pruned timely ideas + dated backups |

## 1. Status markers (required)

Every idea line is `N. [status] text`:

- `[ ]` **unused** — no script exists
- `[~]` **drafted** — a script exists in `../scripts/` but is not published
- `[x]` **shipped** — published; appears in `Content Calendar` / `Title Lab/data/titles.csv`

**Only `[ ]` lines count toward the 50-idea floor.** The header of each file reports unused
count, not total lines, so a growing file can no longer disguise a shrinking backlog.

## 2. Throttle gate (required)

The Idea Loop is no longer an unconditional weekly top-up. Before generating anything:

1. Count `[ ]` lines per channel.
2. **If every channel has ≥ 75 unused ideas → do not generate. Exit with a one-line report.**
3. If any channel is below 75, top **only that channel** back up to 100.

Rationale: three channels publish roughly 3–5 Shorts/week combined. A 75-idea floor is
~4 months of runway per channel.

## 3. Pruning (required, every run)

Timely ideas decay. On every run, before adding:

- Move any `[timely]`, `[competitor]`, or SEO-keyword idea **older than 30 days** into
  `archive/<channel>-timely-archive.md` with its date.
- Never prune evergreen or `[winner-bias]` ideas.
- Renumber the remaining list consecutively.

Date resolution order: inline ISO date in the line → inline `Mon YYYY` → the date of the
enclosing section header.

## 4. Winner bias (conditional)

Bias new ideas toward `winners.json.top_topics` **only when that file reports usable data
quality.** As of 2026-09-05 it reports `LOW` and zero chosen titles carry view counts, so
`top_topics` is a *format prior, not evidence* — label such ideas `[winner-bias]` and keep
them to at most a third of a batch.

See `Metrics Tracker/measurement-gap-2026-09-05.md` for what must be backfilled first.

## 5. Production order (required)

Scripts are pulled from `production-queue.md`, not round-robin across channels. The queue is
weighted by measured average views (currently finance 50% / tech 30% / history 20%). Reweight
whenever `winners.json` is regenerated from real data.
