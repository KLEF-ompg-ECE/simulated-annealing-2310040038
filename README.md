# Assignment 1 — Simulated Annealing: Exam Timetable Scheduling
## Observation Report

**Student Name  :** Shaik Mohammed Awaiz   
**Student ID    :** 2310040038  
**Date Submitted:** March 25, 2026  

---

## How to Submit

1. Run each experiment following the instructions below
2. Fill in every answer box — do not leave placeholders
3. Make sure the `plots/` folder contains all required images
4. Commit this README and the `plots/` folder to your GitHub repo

---

## Before You Begin — Read the Code

Open `sa_timetable.py` and read through it. Then answer these questions.

**Q1. What does `count_clashes()` measure? What value means a perfect timetable?**

```
 It measures the total number of exam scheduling conflicts (clashes) for all students, where a clash means a student has two exams scheduled in the same time slot. A value of 0 means a perfect timetable with no clashes. 
```

**Q2. What does `generate_neighbor()` do? How is the new timetable different from the current one?**

```
 It creates a new timetable by moving one randomly chosen exam to a different time slot. The new timetable differs from the current one by only one exam being assigned to a new slot.
```

**Q3. In `run_sa()`, there is this line:**
```python
if delta < 0 or random.random() < math.exp(-delta / T):
```
**What does this line decide? Why does SA sometimes accept a worse solution?**

```
This line decides whether to accept the new timetable. If the new timetable is better (delta < 0), it is always accepted. If it is worse, it may still be accepted with a probability that decreases as the solution gets worse or as the temperature T decreases. This allows simulated annealing to escape local minima by sometimes accepting worse solutions.
```

---

## Experiment 1 — Baseline Run

**Instructions:** Run the program without changing anything.
```bash
python sa_timetable.py
```

**Fill in this table:**

| Metric | Your result |
|--------|-------------|
| Number of iterations completed |1379 |
| Clashes at iteration 1 | 12|
| Final best clashes |3 |
| Did SA reach 0 clashes? (Yes / No) |No |

**Copy the printed timetable output here:**
```
 Final Timetable
------------------------------------------
  Slot 1:  Geography
  Slot 2:  Chemistry, English
  Slot 3:  History, Computer Science, Economics
  Slot 4:  Biology, Statistics
  Slot 5:  Mathematics, Physics
------------------------------------------
```

**Look at `plots/experiment_1.png` and describe what you see (2–3 sentences).**  
*Where does the biggest drop in clashes happen? Does the curve flatten out?*
```
The number of clashes drops steeply in the initial iterations, showing rapid improvement. After the initial drop, the curve flattens out, indicating that further improvements become rare as the algorithm converges
```

---

## Experiment 2 — Effect of Cooling Rate

**Instructions:** In `sa_timetable.py`, find the `# EXPERIMENT 2` block in `__main__`.  
Copy it three times and run with `cooling_rate` = **0.80**, **0.95**, and **0.995**.  
Save plots as `experiment_2a.png`, `experiment_2b.png`, `experiment_2c.png`.

**Results table:**

| cooling_rate | Final clashes | Iterations completed | Reached 0 clashes? |
|-------------|---------------|----------------------|--------------------|
| 0.80        |     8          |       300               |    No                |
| 0.95        |     3          |      900                |    No                |
| 0.995       |     3         |        1379              |    No                |

**Compare the three plots. What do you notice about how fast vs slow cooling affects the result? (3–4 sentences)**  
*Hint: Fast cooling = temperature drops quickly. Does it have time to explore well?*
```
When the cooling rate is low (0.80), the temperature decreases very quickly, which causes the algorithm to stop exploring new solutions early. As a result, it converges faster but may get stuck with a higher number of clashes.
```

**Which cooling_rate gave the best result? Why do you think that is?**
```
The cooling rate of 0.995 gave the best result because it cools the temperature slowly, allowing the algorithm more time to explore different timetable configurations.
```

---

## Summary

**Complete this table with your best result from each experiment:**

| Experiment | Key setting | Final clashes | Main finding in one sentence |
|------------|-------------|---------------|------------------------------|
| 1 — Baseline | cooling_rate = 0.995 | 3|Simulated Annealing gradually reduced clashes and converged to a stable timetable with 3 conflicts |
| 2 — Cooling rate | cooling_rate = ___ |3 | A slower cooling rate allowed better exploration and produced the best timetable with fewer clashes|

**In your own words — what is the most important thing you learned about Simulated Annealing from these experiments? (3–5 sentences)**
```
From these experiments, I learned that Simulated Annealing is a powerful optimization technique that balances exploration and exploitation. It starts by allowing larger changes, even if they worsen the solution, which helps in avoiding local optima. As the temperature decreases, the algorithm becomes more focused and gradually stabilizes on a better solution.
```

---

## Submission Checklist

- [x] Student name and ID filled in
- [x] Q1, Q2, Q3 answered
- [x] Experiment 1: table filled, timetable pasted, plot observation written
- [x] Experiment 2: results table filled (3 rows), observation and answer written
- [x] Summary table completed and reflection written
- [x] `plots/` contains: `experiment_1.png`, `experiment_2a.png`, `experiment_2b.png`, `experiment_2c.png`
