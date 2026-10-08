# PreTxSim — Event Contracts Hackathon Submission

## Pitch

PreTxSim is a local, air-gapped EVM simulation proxy that lets you **rehearse event-driven contract calls before they fire**: simulate the trigger, preview state changes, gas costs, and emitted logs — then decide whether to broadcast.

## Track Alignment: Web3 Event Tooling

- **Condition-trigger preview**: simulate an event-driven call against live state to answer "will the condition fire, at what gas, with what side effects?"
- **Log inspection**: `RiskInspector` captures emitted logs and storage diffs pre-execution, so event consumers can validate the payload before it exists on-chain.
- **Gas visibility**: exact gas usage reported before broadcast — no surprise costs on automated triggers.
- **Gate**: interactive approve/refuse, or `--ci` mode for fully automated event pipelines.

## Quick Start

```bash
docker compose up -d
```

See [demo_runbook.md](demo_runbook.md) for evaluator instructions.

## Key Features

- Air-gapped `revm` simulation — no keys broadcast until accepted
- RiskInspector: delegatecalls, selfdestructs, storage writes, allowances, EIP-7702, emitted logs
- Local LLM advisory (Ollama `smollm2`), zero telemetry
- Drop-in RPC proxy on `http://127.0.0.1:8545`
- `--ci` mode: structured JSON + exit codes

## Demo

- [docs/assets/demo.mp4](docs/assets/demo.mp4)
- Payloads: [examples/demo_txs.json](examples/demo_txs.json)
