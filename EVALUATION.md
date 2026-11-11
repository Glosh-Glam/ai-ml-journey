# Evaluation

## How to submit a week
1. Work on a branch: `git checkout -b week-NN`
2. Push it, then open Claude Code in this repo and say: **"evaluate week NN"**
3. Claude Code checks out the branch, **runs your code and tests**, and scores the work against the rubric below. It writes the review to `reviews/weekNN.md`, updates the scoreboard, and merges into `main` if the work passes (score ≥ 14/20).
4. If it doesn't pass, fix what the review lists and ask again.

## Rubric (each item scored 0–4, total out of 20)
| Axis | 4 = excellent | 0 = missing |
|------|--------------|-------------|
| **Works** | Runs from a clean clone with the README steps, and tests pass | Doesn't run |
| **Correct** | Metrics, splits, and logic are sound, with no data leakage, and it handles edge cases | Wrong results |
| **Milestone met** | Every 🛠 deliverable for the week is there | Most are missing |
| **Engineering** | Clean structure, no secrets in git, typed I/O, logging, reproducible (pinned deps, seeds) | Notebook spaghetti |
| **Explains it** | RESULTS/SPEC/DESIGN docs say *why*, with numbers, and you can answer 3 oral questions | No write-up |

Each review ends with **3 oral-defense questions** (the "deliverable you can defend" part of the syllabus). Answer them in `reviews/weekNN.md` before the next week starts.

## Scoreboard
| Week | Project | Score /20 | Status | Review |
|------|---------|-----------|--------|--------|
| 1 | Pulse | – | not started | – |
