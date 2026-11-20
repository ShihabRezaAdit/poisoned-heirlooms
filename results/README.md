# `results/`

Aggregate CSVs and per-seed JSONs backing every number in the paper. Raw model
generations and intermediate checkpoints are kept out of version control.

## Layout

```
results/<EXP_ID>/
├── aggregate/     # paper-ready CSVs (installation, survival, utility, stage comparison)
├── per_seed/      # one JSON per model/seed, both judges, triggered + untriggered
├── manifests/     # provenance and config hashes
└── ...            # per-operation detail (merge, chain, bootstrap, per-source, ...)
```

## Experiment IDs

| ID | Model | Poison rate |
|----|-------|:-----------:|
| `E1`  | Qwen2.5-7B   | 20% (primary) |
| `E1b` | Qwen2.5-7B   | 10% |
| `E9a` | Llama-3.1-8B | 20% |
| `E9b` | Mistral-7B   | 20% |

## Key files

| Paper item | File |
|------------|------|
| Installation strength (Table 1) | `<ID>/aggregate/e1_model_metrics.csv` |
| Survival ratios (Table 2, Figure 2) | `<ID>/aggregate/e1_survival.csv` |
| Utility / IFEval | `<ID>/aggregate/e1_utility.csv` |
| Human-judge validation | `human_validation/` |

Net ASR = triggered harmful-compliance rate minus untriggered rate.
Survival ratio `S` = derivative net ASR / ancestor net ASR.
