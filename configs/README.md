# `configs/`

Configuration is split into two kinds, kept strictly apart.

| Kind | Location | Hardware-dependent? | Hashed into the run ID? |
|------|----------|:-------------------:|:-----------------------:|
| **Scientific** (per experiment condition) | `configs/<EXP_ID>/*.yaml` | No | Yes |
| **Engineering / runtime** | `configs/runtime/` | Yes | No (recorded in provenance) |
| **Templates** | `configs/templates/` | n/a | n/a |

**Rules**

- No value that affects a result is passed on the command line; it lives here.
- A run whose scientific-config hash matches no file here is not reportable.
- `models.yaml` and dataset revisions are pinned so results are reproducible.

**Experiment IDs**

| ID | Model | Poison rate |
|----|-------|:-----------:|
| `e1`  | Qwen2.5-7B   | 20% |
| `e1b` | Qwen2.5-7B   | 10% |
| `e9a` | Llama-3.1-8B | 20% |
| `e9b` | Mistral-7B   | 20% |

`e2`-`e4` and `ed` hold the derivation-operation settings (continued fine-tuning,
merging, distillation); `eval/` holds the evaluation protocol; `smoke/` holds
technical plumbing checks that are not experiments.
