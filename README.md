# Summatic

A mental arithmetic speed trainer that times every problem individually, finds the category costing you seconds, and points you at the technique that fixes it.

Most arithmetic trainers give you one number at the end. That tells you whether you're improving but not what to work on. Summatic logs the latency on every single answer and tags it by the method that solves it fastest, so a session ends with a diagnosis instead of a score: *your slowest category was dividing by 7 at 5.1s — drill reverse multiply.*

Built for people preparing for the timed arithmetic screens at quantitative trading firms, where the standard format is roughly 80 questions in 8 minutes — about six seconds per question.

**Live:** _(add your URL once the domain is pointed)_

## What's in it

**Six operation families.** Addition, subtraction, multiplication, division, percents, and decimals. Percents and decimals are the most commonly skipped and most commonly tested; they include fraction-to-decimal conversion, percent change, and applying an increase or cut.

**Per-problem latency.** Every answer is timed. Results break down by operation and by 28 method tags — pairs straddling a midpoint, multiplying by 11, subtraction from a round number, dividing by 7, and so on.

**The heat ribbon.** A live strip that appends one bar per answer, coloured on a temperature ramp anchored to interview pace: 6.0s reads as a cold ember, 1.5s is white hot. Misses render cold slate rather than red — a miss is heat you didn't generate. The ribbon you watch during the drill is the same object that becomes your analytics chart when the clock stops.

**Four modes.**

| Mode | What it does |
|---|---|
| Practice | Misses cost nothing. Default. |
| Interview sim | Misses subtract a point, matching penalised screens. |
| Adaptive | Weights problem selection toward the categories your history says are slow. |
| Recognition | Shows a problem and asks which method applies — without solving it. |

Recognition mode exists because naming the method is a separate skill from executing it, and it's the one people skip. Most trainees can do difference of squares when told to; far fewer spot that `47 × 53` is a difference-of-squares problem in under half a second. That recognition step is where the time actually goes.

**Seeded method patterns.** Rather than waiting for technique-shaped problems to appear by chance, the generator deliberately mixes them in — pairs straddling a round midpoint, ×11, ×25, complement subtraction. Toggleable.

**A methods reference** built into a drawer, deep-linked from your results. Seventeen techniques with worked examples.

## Running it

It's one file with no build step and no dependencies beyond two webfonts.

```bash
git clone https://github.com/USERNAME/summatic.git
cd summatic
python3 -m http.server 8000   # or just open index.html
```

## Deploying

Push to a GitHub repo, then **Settings → Pages → Source: Deploy from a branch → `main` / `root`**.

For a custom domain, put the bare domain in `CNAME` (no protocol, no trailing slash), then at your registrar add:

- An `ALIAS`/`ANAME` record on the apex pointing to `USERNAME.github.io`, or four `A` records to `185.199.108.153`, `185.199.109.153`, `185.199.110.153`, `185.199.111.153`
- A `CNAME` record on `www` pointing to `USERNAME.github.io`

DNS takes anywhere from ten minutes to a day. Tick **Enforce HTTPS** in Pages settings once the certificate provisions.

## Data and privacy

There is no backend, no account, and no analytics. Session history and per-tag statistics live in `localStorage` in your own browser, and **Export data** dumps everything to JSON. Nothing is transmitted anywhere. In contexts where storage is blocked — private browsing, sandboxed iframes — the app detects it, falls back to in-memory state, and says so in the footer rather than failing silently.

## How to actually use it

Ten focused minutes daily beats one long weekend session. This skill decays fast and rebuilds fast.

1. **Weeks 1–2 — isolation.** One operation at a time, 1:00 drills, practice mode. Build the execution before the recognition.
2. **Weeks 3–4 — recognition.** Alternate recognition mode with 2:00 mixed drills. Widen multiplication to 2–99 × 2–99. Expect your score to drop when you do; that's the point.
3. **Week 5 onward — under pressure.** 8:00 interview sim with the penalty on. Log the number daily, not the feeling.

Two failure modes worth naming: memorising answers rather than techniques, which fails the moment you see an unfamiliar problem; and stopping once you hit a score you're happy with.

## Contributing

Issues and pull requests welcome. Useful directions: more method tags, keyboard-only navigation of the results tables, a shareable session permalink, additional operation families (roots, logs, compounding).

## License

MIT. Use it, fork it, deploy your own.
