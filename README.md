<h1 align="left">Hi, I'm Abhinav</h1>

<h3 align="left">I build <a href="https://github.com/0xLittleDream/embertail">EmberTail</a>: tests that check whether AI agents keep money correct.</h3>

When an AI agent pays, sending the money is the easy part. The hard part is knowing what really happened when the reply gets lost. EmberTail sets up a payment, breaks one thing on purpose (a timeout, a lost reply, a failed send), and then checks the money record independently, instead of trusting what the agent says.

<p align="left">
  <a href="https://embertail.xyz"><img alt="embertail.xyz" src="https://img.shields.io/badge/embertail.xyz-visit-f2591d?style=flat-square"></a>
  <a href="https://github.com/0xLittleDream/embertail/releases/latest"><img alt="Money Check release" src="https://img.shields.io/github/v/release/0xLittleDream/embertail?style=flat-square&color=f2591d&label=Money%20Check"></a>
  <a href="https://github.com/0xLittleDream/embertail/actions/workflows/ci.yml"><img alt="CI" src="https://img.shields.io/github/actions/workflow/status/0xLittleDream/embertail/ci.yml?style=flat-square&label=CI"></a>
  <a href="https://github.com/0xLittleDream/embertail/blob/main/FINDINGS.md"><img alt="Findings" src="https://img.shields.io/badge/findings-fixed%20%26%20credited-2ea043?style=flat-square"></a>
</p>

<picture>
  <source media="(prefers-color-scheme: dark)" srcset="https://raw.githubusercontent.com/0xLittleDream/embertail/main/assets/stats-dark.svg">
  <img alt="200,000+ money checks run, 9,000+ scenario runs, 30+ projects tested, 25+ confirmed findings; 57 agent scenarios, 14 money rules, 12 projects notified" src="https://raw.githubusercontent.com/0xLittleDream/embertail/main/assets/stats-light.svg" width="100%">
</picture>

## Fixed after our reports

| Project | What we found | Their fix |
|---|---|---|
| **[ClawRouter](https://github.com/BlockRunAI/ClawRouter)** (BlockRun) | A per-run spending cap could be beaten by requests running at the same moment, and a paid request whose reply was lost was paid again | [PR #440](https://github.com/BlockRunAI/ClawRouter/pull/440), merged the same day, **credited** |
| **[Franklin](https://github.com/BlockRunAI/Franklin)** (BlockRun) | An AI agent with a wallet paid the same invoice twice after a lost reply, and recorded paid invoices as "unpaid" | Payment hold moved into code in [3.49.7](https://github.com/BlockRunAI/Franklin/releases/tag/v3.49.7); EmberTail **named** in the [3.49.9 notes](https://github.com/BlockRunAI/Franklin/releases/tag/v3.49.9) |
| **[NOFX](https://github.com/NoFxAiOS/nofx)** | One x402 request could produce several redeemable payment authorizations | [PR #1549](https://github.com/NoFxAiOS/nofx/pull/1549), merged the next day |

More findings are with their projects under coordinated disclosure. They are listed in [FINDINGS.md](https://github.com/0xLittleDream/embertail/blob/main/FINDINGS.md) only once fixed or public.

## Open-source contributions

- **[coinbase/agentkit](https://github.com/coinbase/agentkit)**:
  - [PR #1597](https://github.com/coinbase/agentkit/pull/1597): the Python ERC-20 transfer and swap approval now read the integer receipt status, so success and failure are reported correctly.
  - Reported in [#1558](https://github.com/coinbase/agentkit/issues/1558) and [#1592](https://github.com/coinbase/agentkit/issues/1592).
- **[apache/apisix](https://github.com/apache/apisix)**: [PR #14097](https://github.com/apache/apisix/pull/14097) documents `cost_expr` examples for each API format in AI rate limiting.

## Projects

| | |
|---|---|
| **[EmberTail Money Check](https://github.com/0xLittleDream/embertail)** | A free, open-source self-test for AI agents that handle money. It runs 57 payment scenarios on a simulated ledger against 14 money rules, keeps replayable evidence, and includes a GitHub Action for CI. |
| **[Smart Bell System](https://github.com/0xLittleDream/Smart-Bell-Sys)** | An automated school bell on an ESP32. It has a real-time clock schedule, a Wi-Fi timetable editor, an OLED status display and relay switching, and it keeps time through power cuts. |
| **[PWEnhancer](https://github.com/0xLittleDream/PWEnhancer)** | A Chrome extension for online lectures. It skips silences, tracks study time, predicts how much time is left, and allows faster playback. |

## How I work

- **Report privately first.** I publish only after a fix is available or 90 days have passed.
- **Reproduce first.** Every finding is reproduced on the project's own published code, with a control run that behaves correctly.
- **Correct our mistakes in public.** When we get something wrong, we say so: see the [errata](https://github.com/0xLittleDream/embertail/blob/main/ERRATA.md).

<sub>What my projects are built with: TypeScript · Node.js · viem · x402 · Base and Base Sepolia · GitHub Actions · Cloudflare Workers · ESP32 / C++</sub>
