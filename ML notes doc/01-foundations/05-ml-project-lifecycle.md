# 05 — The Machine Learning Project Lifecycle

**Estimated time:** 15–20 minutes  
**Prerequisites:** Lessons 01–04  
**Goal:** understand that building an ML model is only one part of an ML project.

## The full picture

```mermaid
flowchart TD
    A[Define the problem] --> B[Collect and clean data]
    B --> C[Split the data]
    C --> D[Train a model]
    D --> E[Test on unseen data]
    E --> F{Good enough?}
    F -- No --> G[Improve data or model]
    G --> D
    F -- Yes --> H[Use the model]
    H --> I[Monitor performance]
```

The process is a loop, not a straight line. If the model fails, we may need better data, a clearer target, a simpler approach, or even a different problem definition.

## What each step means

1. **Define the problem:** decide what prediction is needed and how success will be measured.
2. **Inspect the data:** understand what each row means, check missing values, and look for mistakes.
3. **Build a baseline:** start with a simple rule or model so we have something to compare against.
4. **Train:** let the chosen algorithm learn patterns from the training examples.
5. **Evaluate:** test predictions on examples not used to fit the model.
6. **Inspect errors:** find where and why the model fails.
7. **Package and test:** make the code reliable and easy for someone else to run.
8. **Deploy and monitor:** if people will use it, watch for failures and changes in the data.

## A concrete example: canteen demand

Suppose a canteen wants to estimate how many lunches to prepare.

- **Problem:** predict the number of lunches needed tomorrow.
- **Data:** past daily sales, weekday, and known events.
- **Baseline:** predict the average for that weekday.
- **Model:** try a regression model.
- **Evaluation:** test on later dates the model did not train on.
- **Errors:** check whether it misses special-event days.
- **Use:** show a forecast with uncertainty to the staff.
- **Monitor:** compare predictions with actual sales over time.

We should not claim that the model reduces waste until a real evaluation supports that claim.


## Quick checkpoint

1. Why build a baseline before a complicated model?
2. Why should evaluation use data that was not used for training?
3. If the model fails, must we always choose a more complex algorithm?
4. What should we monitor after deployment?

<details>
<summary>Answers</summary>

1. It gives a simple reference point to beat.
2. To estimate how well the model may work on new cases.
3. No. The issue may be data quality, the target, the split, or the choice of metric.
4. For example, input-data changes, prediction quality when labels become available, errors, latency, and service failures.
</details>

## Next lesson

[06 — Where ML Helps, and Where It Does Not](06-when-ml-is-useful.md)
