[README.md](https://github.com/user-attachments/files/33239402/README.md)
# PTARF: Permission- and Trust-Aware Retrieval Framework

Code, synthetic benchmark and results for the manuscript "PTARF: An Identity-based Permission and Trust-Aware Retrieval Framework for Dynamic Cloud Environments" (Urvashi Rahul Saxena, Rajkumar Buyya, Ramin Karim, Ravdeep Kour).

PTARF decides each request in a fixed order: a deterministic policy gate (role–resource–action rules, conditions, account status), then a restrictive behavioural trust score. Retrieval is limited to the requester's own role before ranking, and a large language model only explains the decision.

## Contents

| Path | Description |
|---|---|
| `PTARF_Executable_Code.ipynb` | Colab notebook (executed, with outputs). Contains the benchmark generator, all evaluation code, and every table and figure of the manuscript. |
| `data/` | The five synthetic benchmark datasets (`seed0`–`seed4`), `DATA_DICTIONARY.csv`, `README_DATASET.md` and `SHA256SUMS.txt`. |

## Reproduce the results

1. Open the notebook in Google Colab (a CPU runtime is enough):
   `https://colab.research.google.com/github/<USER>/<REPO>/blob/main/PTARF_Executable_Code.ipynb`
2. Keep `QUICK = False` in the setup cell. This reproduces the five-seed results in the manuscript and takes about 45–90 minutes. `QUICK = True` (about 10–25 minutes) only checks that the pipeline runs; its numbers differ slightly.
3. Choose "Runtime → Run all. The last cell compares the recomputed values with the manuscript and prints `All values within tolerance`.

Retrieval uses TF-IDF with cosine similarity. The LLM explanation stage is not part of any reported number. Latency values depend on the machine and will vary between runs.

## Benchmark

Fully synthetic, no personal data. Each seed has 5,000 users, a 120-day behaviour history, 50,000 requests and one policy document per rule. Labels come from eight named scenarios, never from any model. The generator is deterministic for a given seed, so the notebook regenerates identical files; to check the released files, run `sha256sum -c SHA256SUMS.txt` inside `data/`. File descriptions: `data/README_DATASET.md`.

Contact

Dr. Urvashi Rahul Saxena (corresponding author): usaxena@mit.edu.au
