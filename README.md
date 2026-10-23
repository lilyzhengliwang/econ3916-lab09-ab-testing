# econ3916-lab09-ab-testing

# A/B Testing — Designing the Data-Generating Process

## Objective
I wanted to see why random assignment matters for reading a difference in outcomes as a causal effect, and how to test and size an A/B test, using the LaLonde job training experiment and the Cookie Cats mobile game test.

## Methodology
* Loaded the LaLonde NSW job training experiment (445 people: 185 trainees and 260 controls) and computed the experimental ATE as the difference in mean 1978 earnings.
* Simulated an observational comparison group in place of the randomized controls to show selection bias, and split the gap: Observational ATE = True ATE + Selection Bias.
* Ran a permutation test (9,999 shuffles) and a bootstrap BCa 95% confidence interval for the ATE.
* Ran a power analysis: the power of this study, and the sample size needed to detect three different dollar effects.
* Applied the same three steps (difference in means, permutation test, bootstrap) to the Cookie Cats mobile game A/B test (90,189 players, first gate at level 30 or level 40, Day-1 retention).
* Wrote a sample-size function, `n_needed()`, checked it against the power analysis, and used it to size a rerun of Cookie Cats.

## Key Findings
* In the experiment, trainees earned $1,794.34 more than controls (permutation p = 0.0046, 95% CI $575.18 to $3,262.37).
* The simulated comparison group gave an ATE of -$14,784.45. The sign flipped because the comparison group was very different from the trainees to begin with, so the gap mostly reflects selection bias and not the effect of the training. Random assignment is what removed that problem in the experiment.
* In Cookie Cats, moving the gate from level 30 to level 40 changed Day-1 retention by 0.59 percentage points in favor of level 30 (p = 0.0752). The evidence is not strong enough to say the difference is real, so I would not move the gate based on this test alone.
* If the company believes the 0.59 percentage point difference is real and wants to confirm it, a rerun would need 111,192 players per group.
