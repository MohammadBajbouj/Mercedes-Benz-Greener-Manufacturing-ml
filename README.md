# Faster tests, greener cars – Mercedes-Benz Greener Manufacturing

**Can we predict how long each Mercedes-Benz car stays on the end-of-line test bench?**
ML project (neuefische AI PM bootcamp, October 2026) on the public Kaggle data set *Mercedes-Benz Greener Manufacturing* (2017).

## Hypothesis (H2)
*Does the same car configuration always need the same test time?*
**Answer: no.** Cars with exactly the same configuration (all 376 columns identical) still differ by about 8 seconds. Using the configuration as indicator, at most about 60 % of the differences in test time between cars can be predicted – the rest comes from the test itself.

## Key results
| | Result |
|---|---|
| Data | 4,209 tested cars, 376 anonymised columns (8 text, 368 yes/no), test time 72–265 s |
| Limit | about 60 % of the differences in test time can be explained (from 515 cars in 217 groups of identical cars) |
| One column, X0 | alone explains 57.5 % of the differences |
| Three algorithms | Ridge 58.7 %, Random Forest 58.9 %, XGBoost 59.3 % (5-fold cross-validation, 4,208 cars) – equal |
| Final model | Ridge with X0 only: typical miss 12.4 s → 8.0 s (about 4.5 s better per car); 91 of 100 cars within 10 s |
| Kaggle check | 54.1 % on 4,209 hidden cars = 97 % of the competition winner's score (55.6 %) |
| Long tests | cannot be predicted from the configuration – future work: record test-run data |

## Repository contents
| File / folder | Content |
|---|---|
| [`04_mercedes_eda_and_modeling.ipynb`](04_mercedes_eda_and_modeling.ipynb) | The project notebook: EDA, H2 limit, baseline, three algorithms, error analysis, Kaggle submission, long tests (Steps 1–29) |
| [`my_notes/machine_learning_presentation_stakeholder_deck_v4_final.pptx`](my_notes/) | Presentation for a non-technical audience (12 main slides + explanation slides) |
| [`my_notes/machine_learning_presentation_deck_v8.pptx`](my_notes/) | Detailed engineering deck with references to the project's internal decision log |
| `01_assignment.md`, `02_kanban_board.md`, `03_eda-and-modeling.ipynb`, `assets/` | Course material from the neuefische ML project template |
| `pyproject.toml`, `uv.lock` | Python environment |

## Setup
```bash
uv sync
```
The Kaggle data is not part of this repository. Download it from the competition page
([kaggle.com/c/mercedes-benz-greener-manufacturing](https://www.kaggle.com/c/mercedes-benz-greener-manufacturing)) and put `train.csv` and `test.csv` into `data/`. Then open `04_mercedes_eda_and_modeling.ipynb` in VS Code with the `.venv` kernel and run all cells.

---
© 2026 Mohammad Bajbouj. All rights reserved. Decisions and expert views by Mohammad Bajbouj; text and code drafted with Claude by Anthropic (Claude Cowork, Claude Code) – no ownership of AI-generated text or code claimed. Practice project, neuefische AI PM bootcamp. Course material from neuefische and Kaggle data (Mercedes-Benz) are not covered by this copyright notice.
