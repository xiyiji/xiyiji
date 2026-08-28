## Mengyun Wang

**AI Engineer — evaluation and ML systems**
MS Computer Science, Northeastern University

I work on the part of machine learning that decides whether a model is actually fit to
ship: calibration, offline evaluation, and measuring what breaks when the data a model
sees in production stops looking like the data it was trained on.

---

### [Cognitive Shorts](https://github.com/PSCRedefine) — four services, one engagement model

An engagement prediction system taken from notebook to something operable, as four
deployable FastAPI services: a leakage-safe feature pipeline, cost-aware model selection
under a paired-bootstrap tie test, an operating point chosen against a traffic budget
rather than by maximising F1, then model introspection and drift monitoring around it.

Four candidate models finished statistically tied — every gap's confidence interval
included zero — so operating cost broke the tie. The shipped artefact is **1,958× smaller**
and 35× faster than the runner-up, with no measurable loss.

Docker images running as non-root, per-row fault isolation so one bad row never fails a
batch, request-logging middleware that cannot break a request, and traceability documents
mapping every requirement to its implementation and evidence.

`292 tests` · `CI on Python 3.11 / 3.12 / 3.13` · `MIT`

### [KuaiRand Lab](https://github.com/PSCRedefine/kuairand-lab) — unbiased offline evaluation on real short-video logs

Kuaishou injected uniformly random videos into live recommendation feeds for two weeks.
Training on algorithmic exposure and testing on **both** mechanisms across the identical
calendar window isolates exposure bias from temporal drift.

The cost turns out to be asymmetric:

|  | algorithmic | uniform random |  |
|---|---|---|---|
| Lift @ top 23.9% | 3.428× | 3.363× | **−2.0% — transfers** |
| Mean predicted ÷ actual | 0.96× | **2.07×** | **breaks** |

Ranking survives the shift almost intact. Calibration collapses — the model is twice as
confident as reality on traffic it did not select. A team validating offline would watch
the ranking hold, conclude the model transfers, and ship probabilities that are silently
wrong. **Calibration is a property of the exposure policy, not of the model:** fit a
calibrator on randomized logs and it ships there and is rejected on served traffic, by
almost exactly the same factor in the other direction.

`ROC-AUC 0.8811` · `2.6M interactions` · `every figure reproduces from a committed JSON artefact`


---

The lab was built to test a limitation Cognitive Shorts had published about itself — that
its offline lift was never validated against a randomized holdout. It also overturned that
project's headline: a measured signal ceiling of 0.58 ROC-AUC turned out to be a property
of the synthetic data's corrupted joins, not of engagement prediction. On real logs a
single feature reaches 0.7486.

Each repository documents what is known to be wrong with it before it documents what works.

📫 btzdnsn@gmail.com
