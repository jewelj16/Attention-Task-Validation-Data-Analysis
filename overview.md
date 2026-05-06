# Attention Validation Experiment — Overview

---

## 1. Background and Objective

The central goal of this study is to **validate a newly developed Selective Attention Game** by comparing performance on it against a standard laboratory attention task, which serves as the gold standard.

Selective attention — the ability to focus on relevant targets while filtering out irrelevant distractors — is one of the most studied constructs in cognitive psychology. The conventional way to measure it is a controlled lab-based visual search task: a participant sits at a computer, a display of coloured squares appears, and they must click the target as quickly and accurately as possible. This method has well-established validity and reliability. Its limitation is practical — it requires a lab, a computer, a trained experimenter, and a participant who can physically attend.

A gamified version of the same task on a smartphone eliminates all of those constraints. It can be deployed remotely, administered without a researcher present, and completed in everyday settings. The question is whether it still measures the same underlying cognitive construct. If performance on the game correlates with performance on the lab task, and if the game shows the same sensitivity to difficulty manipulation (more targets = harder), then the game can be considered a valid substitute.

This process of comparing a new measure against an established one is known as **concurrent validity testing**, and it forms the backbone of this experiment.

---

## 2. Study Design

### 2.1 Design Type

The experiment uses a **2 × 2 Mixed Factorial Design**. There are two independent variables: one manipulated between participants and one manipulated within participants.

```
                        MODALITY  (within-subjects)
                       ┌────────────────┬────────────────┐
                       │      Lab       │      Game      │
  TARGET    ───────────┼────────────────┼────────────────┤
  LOAD      Single     │   Cell A       │   Cell B       │
  (between) ───────────┼────────────────┼────────────────┤
            Multiple   │   Cell C       │   Cell D       │
                       └────────────────┴────────────────┘

  Cell A: Single Target, Lab       (participants 1–21)
  Cell B: Single Target, Game      (participants 1–21)
  Cell C: Multiple Target, Lab     (participants 22–37)
  Cell D: Multiple Target, Game    (participants 22–37)
```

Each participant contributes data to exactly two cells — the two in their row. The design is "mixed" because one factor is between-subjects and the other is within-subjects.

### 2.2 Independent Variables

**Factor 1 — Target Load (Between-Subjects, Nominal)**

Participants were randomly assigned to one of two groups before the study began and remained in that group throughout.

- *Single Target:* One coloured target square appears per trial. The participant must find and click it. This is the lower cognitive demand condition.
- *Multiple Target:* Two or more coloured target squares appear simultaneously per trial. The participant must find and click all of them. This demands more from working memory, divided attention, and response execution.

**Factor 2 — Modality (Within-Subjects, Nominal)**

Every participant completed the task in both modalities. The order was counterbalanced: roughly half of each group completed the Lab task first and the Game second; the other half completed the Game first and the Lab second. Counterbalancing controls for practice and fatigue effects that could otherwise be mistaken for a modality effect.

- *Lab:* A PsychoPy-based visual search task run on a desktop computer in a controlled lab environment. Responses via mouse click. Individual trial-level data recorded.
- *Game:* The Selective Attention Game run on a smartphone. Responses via touchscreen tap. Performance recorded as level-level aggregates, not individual trials.

### 2.3 Dependent Variables

| DV | Description | Scale |
|---|---|---|
| **Reaction Time (RT)** | Time from stimulus onset to first response. In the lab: first mouse click after target appears. In the game: `InitialResponseTime` — time to first tap. | Continuous, milliseconds (converted to seconds for analysis) |
| **Accuracy** | Proportion of correct responses. In the lab: whether the first click hit the target (0 or 1 per trial, averaged). In the game: `SuccessRate(%)` divided by 100. | Continuous, ratio scale 0–1 |

A combined speed-accuracy measure may also be computed to account for the speed-accuracy trade-off — participants who sacrifice one for the other would be penalised.

### 2.4 Participants

| Group | Condition | N | Participant IDs |
|---|---|---|---|
| Group A | Single Target (Lab + Game) | 21 | 1 – 21 |
| Group B | Multiple Target (Lab + Game) | 16 | 22 – 37 |
| **Total** | | **37** | |

All 37 participants completed both modalities (Lab and Game). Counterbalancing was applied within each group independently.

### 2.5 Procedure Summary

1. Participants were randomly assigned to Group A (Single Target) or Group B (Multiple Target).
2. Within their group, each participant was assigned a counterbalancing order: Lab-first or Game-first.
3. Session 1: Participants completed their assigned first modality.
4. Session 2: Participants completed their second modality.
5. Data was exported from PsychoPy (lab files) and the game application (phone files) and stored in four separate folders.

---

## 3. Research Questions

### RQ1 — Concurrent Validity

*Is there a significant positive correlation between performance (RT/Accuracy) in the Game and the Lab Task?*

If the Selective Attention Game is a valid measure of the same construct as the Lab Task, participants who perform well in the lab should also perform well in the game. This is tested separately for each group (Single, Multiple) and each DV (RT, Accuracy), giving four correlation tests. A significant positive Pearson r (or Spearman ρ if normality fails) supports concurrent validity.

### RQ2 — Load Effect

*Is performance significantly worse in the Multiple Target condition compared to the Single Target condition?*

This is a manipulation check. If the task genuinely measures attentional capacity, adding more targets should increase cognitive demand and therefore increase RT and decrease accuracy. Group A and Group B are compared using independent samples t-tests, separately for Lab and Game. A significant difference in the expected direction confirms the task is sensitive to attentional load.

### RQ3 — Modality Effect

*Does the gamified interface significantly alter performance compared to the standard lab interface?*

Even if both platforms measure the same thing, the game interface (touchscreen, smaller screen, game framing) might systematically inflate or deflate RT and accuracy. This is tested within each group using paired samples t-tests, since every participant completed both modalities.

### RQ4 — Level Effect

*What is the effect of level progression on performance within the Game?*

Participants progress through multiple levels in a single game session. Performance may improve across levels (learning/practice effect) or deteriorate (fatigue). Examining how RT and accuracy change as a function of Level number reveals whether participants were still adapting to the game during early levels — which would affect how game performance should be interpreted relative to the lab.

---

## 4. Statistical Analyses Required

### 4.1 Descriptive Statistics

For each of the four cells (Single/Lab, Single/Game, Multiple/Lab, Multiple/Game), report:

- Mean (M) and Standard Deviation (SD) for RT in seconds
- Mean (M) and Standard Deviation (SD) for Accuracy as a proportion

All statistics are computed at the **participant level** — trial/level scores are first averaged within each participant, then group statistics are computed — to avoid pseudo-replication.

### 4.2 Correlation — Concurrent Validity (RQ1)

**Test:** Pearson's r (normality met) or Spearman's ρ (normality violated)

For each group and each DV, correlate participant mean Lab score with participant mean Game score. Four correlations total.

- H₀: r = 0
- H₁: r > 0 (one-tailed — positive direction predicted from theory)
- Bonferroni correction across 4 tests: adjusted α = 0.05 / 4 = **0.0125**

### 4.3 Mixed ANOVA 2 × 2 (RQ2, RQ3, and their interaction)

A 2 × 2 mixed ANOVA with Target Load (between) and Modality (within) tests three effects:

- **Main effect of Target Load:** Overall performance difference between Single and Multiple groups (collapsed across modalities) — addresses RQ2
- **Main effect of Modality:** Overall performance difference between Lab and Game (collapsed across load groups) — addresses RQ3
- **Interaction (Load × Modality):** Whether the modality effect differs depending on which load group the participant belongs to

Assumptions to verify: normality per cell (Shapiro-Wilk), homogeneity of variance between groups (Levene's test), sphericity not applicable (Modality has only two levels).

### 4.4 Paired Samples t-test — Modality Effect (RQ3 follow-up)

Within each group separately, compare Lab mean vs. Game mean for the same participants.

- H₀: No difference in RT between Lab and Game
- H₁: RT differs (two-tailed)
- Effect size: Cohen's d_z
- Bonferroni correction across 4 t-tests (2 paired + 2 independent): adjusted α = **0.0125**

### 4.5 Independent Samples t-test — Load Effect (RQ2 follow-up)

Within each modality separately, compare Single group vs. Multiple group.

- H₀: No difference in RT between Single and Multiple
- H₁: Multiple > Single (one-tailed — direction predicted)
- Variant: Welch's t-test (does not assume equal variances)
- Effect size: Cohen's d (pooled SD)

### 4.6 Level Effect Analysis (RQ4)

Inspect whether RT or accuracy changes across game levels. This can be done descriptively (line plot of mean RT by level) or inferentially (Pearson correlation between Level number and RT, or a simple linear regression). A significant learning or fatigue trend informs whether early levels should be treated as practice and excluded.

### 4.7 Reliability (Advanced)

Internal consistency or test-retest reliability of both tasks can be assessed. Split-half reliability across trials (lab) or levels (game), or Cronbach's alpha if multiple items per session, would indicate how stable measurements are within a single session.

---

## 5. The Four Conditions in Detail

### Condition A — Single Target / Lab (Cell A)

**Who:** Participants 1–21 (Group A).

**What happens:** The participant sits at a computer running PsychoPy. Each trial begins with a fixation cross, then a display of coloured squares appears. Exactly one square is the designated target (identified by `target_col`). The participant clicks on it as quickly and accurately as possible. PsychoPy records the time and identity of every click.

**Cognitive demand:** Low. One target, one response. The task measures visual search speed for a single item with no requirement to hold multiple identities in working memory.

**Data recorded:** One row per trial. Trial-level RT and accuracy are derived from raw click timestamps and clicked object names.

---

### Condition B — Single Target / Game (Cell B)

**Who:** Participants 1–21 (Group A) — the same people who did Condition A.

**What happens:** The same visual search challenge — find one target among distractors — delivered through the Selective Attention Game on a smartphone. The participant taps the target. The game saves one summary row per level.

**Key difference from Condition A:** Platform only. The cognitive challenge is identical. Any performance difference between Conditions A and B for the same participant reflects the interface and environment, not a change in task difficulty.

**Data recorded:** One row per level. RT and accuracy are level-level summaries computed by the game engine. Individual tap timestamps are not saved.

---

### Condition C — Multiple Target / Lab (Cell C)

**Who:** Participants 22–37 (Group B).

**What happens:** Same lab setup as Condition A, but each trial presents two or more target squares simultaneously. The participant must find and click all of them. PsychoPy records every click, allowing the full response sequence to be extracted.

**Cognitive demand:** High. Multiple targets must be found, held in working memory, and responded to in sequence. Both selective attention (identifying each target) and divided attention (managing simultaneous targets) are required. RT is expected to be slower and accuracy lower than Condition A.

**Data recorded:** One row per trial. `mouse.time` and `mouse.clicked_name` may contain multiple entries per trial. The first click is used for RT.

---

### Condition D — Multiple Target / Game (Cell D)

**Who:** Participants 22–37 (Group B) — the same people who did Condition C.

**What happens:** The multiple target version of the Selective Attention Game on a smartphone. Multiple target squares appear; the participant must tap all of them. `HitPositions` contains multiple coordinate tuples and `AvgInterTargetTime` becomes meaningful as a sequential response speed measure.

**Cognitive demand:** Highest. Multiple simultaneous targets on an unfamiliar touchscreen interface. Most ecologically valid condition for real-world deployment.

**Data recorded:** One row per level. `HitPositions` format: `(x1,y1);(x2,y2);...`

---

## 6. Data Structure of All Four Conditions

### 6.1 single/lab and multiple/lab — PsychoPy CSV

**File naming:** `<playerid>_<sometext>.csv`
**Row structure:** One row per trial. Non-trial rows (instructions, fixation) are identified by an empty `trials.thisN` field and dropped on loading.

| Column | Type | What it stores |
|---|---|---|
| `participant` | string | Participant label entered at session start in PsychoPy. May be a name, a code, or an arbitrary string. **Not used as the participant ID in analysis** — the integer prefix of the filename is used instead to ensure consistency across folders. |
| `trials.thisN` | float | Zero-indexed trial counter. `0` = first trial, `1` = second, and so on. Rows where this is `NaN` are non-trial rows and are excluded. Becomes `trial_num` in the unified dataframe. |
| `target_col` | string | The PsychoPy object name of the target square the participant was supposed to click, as specified in the stimulus file (e.g. `red_square`, `green_circle`). Used to score accuracy by checking whether the participant's first click matched this name. |
| `trial.started` | float | Absolute time in seconds from `expStart` (the moment PsychoPy launched the experiment) when the trial routine began. Includes any pre-stimulus interval such as a fixation cross. This is the trial clock reference. |
| `square.started` | float | Absolute time in seconds from `expStart` when the target square first appeared on screen. This is the true stimulus onset — the moment from which RT should be measured. The gap `square.started − trial.started` is the pre-stimulus delay and must be subtracted from the click time to isolate the response latency. |
| `mouse.time` | stringified list of floats | All mouse click times during the trial, serialised as a Python list string, e.g. `[0.453]` or `[0.312, 0.789]`. Each value is in seconds **relative to `trial.started`** (not `square.started`). Only the first entry is used for RT. Multiple entries occur when the participant clicked more than once. |
| `mouse.clicked_name` | stringified list of strings | The PsychoPy object name clicked at each time in `mouse.time`, serialised as a list string, e.g. `['red_square']` or `['blue_circle', 'red_square']`. Accuracy is scored 1 if `target_col` appears in the first entry, 0 otherwise. |

**RT formula:**

```
RT = mouse.time[0]  −  (square.started − trial.started)
```

**Timing diagram:**

```
expStart
│
├─── trial.started        (trial routine begins — fixation cross shown)
│         │
│         ├─── square.started   (target square appears on screen)
│         │           │
│         │           └─── participant clicks
│         │                     └─── mouse.time[0]  (relative to trial.started)
│         │
│         RT = mouse.time[0] − (square.started − trial.started)
```

**Note for multiple/lab:** Structure is identical. `mouse.clicked_name` may list multiple target names on one trial. The first click is extracted the same way.

---

### 6.2 single/phone and multiple/phone — Game CSV

**File naming:** `<playerid>_attentional_spotter_results.csv`
**Row structure:** One row per completed game level. Individual tap events are not saved — each row is a summary of everything that happened within the level.

| Column | Type | What it stores |
|---|---|---|
| `PlayerID` | string | Player identifier assigned by the game application (e.g. `Player_7`). **Not used as the participant ID** — the filename integer prefix is used for consistency with lab files. |
| `Timestamp` | datetime string | ISO 8601 date-time when the level ended and results were saved (e.g. `2024-03-15T14:32:07`). Not a DV, but useful for verifying session order and counterbalancing. |
| `GameMode` | string | Task variant for the level: `singleTarget` (Condition B) or `multipleTarget` (Condition D). Cross-check against the folder name to confirm correct file placement. |
| `Level` | integer | Level number within the session, starting from 1. Becomes `trial_num` in the unified dataframe. Higher level numbers can be used to examine the level effect (RQ4). |
| `FinalScore` | integer | Composite score computed by the game engine using an internal formula that combines speed, accuracy, and other factors. Not used as a DV because the formula is opaque and does not map cleanly onto RT or accuracy. |
| `Completed` | boolean | `True` if the participant finished the level; `False` if they timed out or exited early. Incomplete levels have potentially truncated or unreliable RT and accuracy values and should be flagged. |
| `SuccessRate(%)` | float | **Primary accuracy measure.** Percentage of targets correctly identified during the level, computed by the game (range 0–100). Divided by 100 to convert to proportion 0–1 for comparability with lab accuracy. Level-level aggregate — individual target outcomes are not recoverable. |
| `HitRate(%)` | float | Percentage of target locations where a hit was registered. May differ from SuccessRate if the game applies partial credit or different counting logic. Retained in the data but not used as the primary accuracy measure. |
| `FalseAlarms` | integer | Count of taps on non-target (distractor) objects during the level. High false alarm counts suggest impulsive or inaccurate responding. Available as a secondary DV. |
| `InitialResponseTime(ms)` | float | **Primary RT measure.** Time in milliseconds from the moment the first target appeared on screen to the participant's first tap. Divided by 1000 to convert to seconds. Conceptually equivalent to the lab RT — both capture latency from stimulus onset to first response. |
| `AvgInterTargetTime(ms)` | float | Average time in milliseconds between consecutive target responses within the level. Only interpretable in the Multiple Target condition. Relevant to RQ4 as a secondary speed measure. |
| `HitPositions(x,y)` | string | Screen coordinates of each successful tap, as a semicolon-separated list of (x, y) tuples. Single target: `(120,340)`. Multiple targets: `(120,340);(450,210);(300,180)`. Counting the opening parentheses gives `n_clicks` in the unified dataframe. |

**Note for multiple/phone:** Structure is identical to single/phone. `GameMode` = `multipleTarget`; `HitPositions` contains multiple semicolon-separated tuples.

---

## 7. Unified Data Structure After Loading

After loading and harmonising all four sources, the analysis uses a single dataframe:

| Column | Source | Description |
|---|---|---|
| `participant` | filename prefix | Integer 1–37, consistent across all four folders |
| `target_load` | folder name | `single` (IDs 1–21) or `multiple` (IDs 22–37) |
| `modality` | folder name | `lab` or `game` |
| `trial_num` | `trials.thisN` / `Level` | Trial or level number within the session (used for RQ4) |
| `RT` | computed (lab) or `InitialResponseTime(ms)/1000` (game) | Reaction time in seconds |
| `accuracy` | computed (lab) or `SuccessRate(%)/100` (game) | Correctness as proportion 0–1 |
| `n_clicks` | `len(mouse.clicked_name)` (lab) or tuple count in `HitPositions` (game) | Number of clicks or taps |

**Participant-level means** are computed from this dataframe (averaging across all trials/levels per participant per condition cell) before running any statistical tests, so that each participant contributes exactly one data point per cell.

---

## 8. Key Differences Between Lab and Game Measurements

These are structural features of the two platforms, not data errors. They affect how results should be interpreted.

| Aspect | Lab (PsychoPy) | Game (Smartphone) |
|---|---|---|
| **RT granularity** | Per trial | Per level (aggregated across all trials in the level) |
| **Accuracy granularity** | Per trial (binary correct/incorrect) | Per level (SuccessRate aggregate) |
| **Input device** | Mouse | Touchscreen |
| **Screen** | Desktop monitor | Smartphone |
| **Environment** | Controlled lab | Uncontrolled |
| **Data logged by** | PsychoPy (trial-by-trial) | Game engine (level-end summary) |
| **Experimenter present** | Yes | No |

The granularity difference is the most analytically significant. The lab produces tens of data points per participant per condition; the game produces one per level. After aggregating to participant means, lab estimates are based on more observations and are therefore more stable. This should be acknowledged when interpreting correlation strength in RQ1 and any effect size estimates across modalities.
