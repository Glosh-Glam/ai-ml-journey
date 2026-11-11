# Claude Code: how to evaluate this repo

When the user says "evaluate week NN":
1. `git fetch && git checkout week-NN`. Read README.md (that week's 🛠 milestone) and the project's README checklist.
2. Actually run it: install deps, run tests and scripts. Never score from reading the code alone.
3. Score with the rubric in EVALUATION.md (5 axes × 0–4). Back up each score with evidence (command output, file:line).
4. Write `reviews/weekNN.md`: score table, what works, must-fix list, nice-to-have, and 3 oral-defense questions.
5. Update the EVALUATION.md scoreboard. If the score is ≥ 14, merge into main and push; otherwise leave the branch open.
6. Don't write the solution for the user. Point to the concept or resource instead. Teaching > fixing.
