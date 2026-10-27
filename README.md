# 🩺 fleet-doctor

**A doctor for agentic AI fleets.** Paste one prompt into any agent to make it self-report its own configuration (the *probe*); then read that intake against opinionated lenses that never simply believe the patient (the *diagnosis*). Like a physician: probe, then diagnose — because a fluent self-report is exactly what a mis-configured agent produces.

> ### 🧱 This is a **brick** (抛磚引玉 — "throw a brick to attract jade")
> It has been dogfooded on exactly **one** fleet (a Claude Code setup) and survived a fresh-lineage skeptic review — but its **portability across other harnesses is untested**. That's the whole reason it's public: **run the probe on *your* fleet and send back what it produced.** Real probe outputs from OpenClaw, Cursor, raw-API agents, LangGraph, custom harnesses — *that* is the jade this brick is fishing for. See [Contributing](#contributing). Treat every claim here as provisional until your samples confirm or break it.

## The two parts

| | file | what it does |
|---|---|---|
| **Part 1 — the probe** | [`probe.md`](probe.md) | Paste it, unedited, into any agent. It self-reports across 9 sections (identity · memory · tools · floors · autonomy · triggers · input-handling · self-modification · unknowns) **plus §J behavioral self-tests** — including a *sycophancy trap* and a *stand-down check*. Every claim is tagged `[TOLD]`/`[VERIFIED]`/`[ASSUMED]`; gaps are marked, never fabricated. |
| **Part 2 — the diagnosis** | [`diagnosis.md`](diagnosis.md) | Reads the intake against **4 lenses** — an opinionated house doctrine, the web/field consensus, the autonomy-ladder (as a translation device, not a scoreboard), and an extensible slot — then adjudicates. The lenses can *disagree*; on safety, the field-standard lens wins. |
| **Worked example** | [`example-diagnosis.md`](example-diagnosis.md) | A synthetic fleet run end-to-end, with real pathologies, so you can see the doctor catch problems rather than rubber-stamp. |
| **Real samples** | [`samples/`](samples/) | Unedited probe outputs from real harnesses, each with a header saying where the probe misfired. First one: [Codex CLI](samples/codex-cli.md). |

## How to use it

1. **Probe** — paste the full contents of [`probe.md`](probe.md) into the agent you want to audit (or into a session of it). Let it fill in sections A–J about itself.
2. **Diagnose** — hand that filled-in intake (plus [`diagnosis.md`](diagnosis.md)) to a *different* model lineage and ask it to score the fleet per the lenses. Fresh lineage matters: an agent grading itself correlates its own blind spots.
3. **Corroborate** — the diagnosis is only as good as its skepticism. Don't accept a `[TOLD]` floor as enforced; make the §J tests actually run.

## The method, in one line

**Adversarial, not credulous.** Agent self-reports and benchmark scores are gameable (every major agent benchmark has been shown exploitable; reward-hacking generalizes to broad misalignment). So the doctor leads with *behavioral* tests, corroborates every claim against an observable artifact, and treats honest "I can't observe that" as a **positive** signal — smooth-and-complete is the red flag.

## About the opinionated lens (Lens 1)

Lens 1 is deliberately a **point of view** — it operationalizes the *evnchn-agentic* thesis: leverage over completion · recoverability over restriction · **identity as a scoped orientation, not an ego** · a hard floor the "dial" can't touch · the human at the pivot, not the hot loop. The fuller thesis is still being written; this repo is the *triggerable slice* of it. Its coinages (`identity-is-upstream-of-floors`, `{FamousPerson}.md`, `orientation-not-ego`) are **house doctrine, corroborated in substance by independent research but not field terminology** — Lens 2 keeps them honest. **If this doctrine isn't yours, swap your own in as Lens 1** (that's what Lens 4 is for). Imposing one identity as universal is the very anti-pattern the doctrine warns against.

## Contributing

The most valuable contribution is **a real probe output from a fleet that isn't Claude Code.** Open an issue or PR with:
- the harness (OpenClaw / Cursor / raw API / LangGraph / custom…),
- the filled-in probe (redact anything private — the probe is designed so a *refusal* or `⧗ NOT OBSERVABLE` is itself a data point),
- optionally, where the probe misfired, got refused as a jailbreak, or produced obvious confabulation.

Samples that **break** the probe's portability are as useful as ones that confirm it. Corrections to the lenses (especially Lens 2, the field-consensus one) are welcome with sources.

## License

MIT — see [`LICENSE`](LICENSE). Use it, fork it, swap the doctrine, tell me what broke.
