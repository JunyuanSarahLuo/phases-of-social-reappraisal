# From Receipt to Implementation: The Dynamics of Social Reappraisal

Data and analysis code for:

Luo, J., Waugh, C. E., & English, T. From receipt to implementation: The dynamics of social reappraisal.

This repository contains the de-identified data and the R Markdown script needed to reproduce every analysis reported in the manuscript and its Supplemental Material.

## Repository contents

| File | Description |
|---|---|
| `PORS_clean.Rmd` | Analysis script. Reproduces all results in the manuscript and Supplemental Material. |
| `PORS_clean.html` | Knitted output of `PORS_clean.Rmd`, for reference. |
| `PORS_task.xlsx` | Trial-level task data (sheet `Clean`), one row per trial. |
| `PORS_survey.xlsx` | Participant-level survey data (sheet `Sheet1`), one row per dyad. |
| `PORS_hours.xlsx` | Hours per week the two dyad members spent together, reported at pre-screening (sheet `Hours`). |

## Structure of the script

The script follows the order in which results appear in the paper.

| Script section | Corresponds to |
|---|---|
| Data preparation | Participant exclusions and construction of all analysis data frames |
| Manuscript: Method | Participants, relationship measures, trial exclusions, role assignment (footnote) |
| Manuscript: Results | ICCs; Tables 1 and 2; Figure 2; mediation (Figure 3, Table S7); experiencer and helper gender (Figure 4, Table S8); relationship length and quality as moderators; assumption checks |
| Supplement | Table S1 (helper demographics), Table S4 (descriptive statistics and correlations), Table S5 (model fit), Table S6 (implementation tactics), exploratory analyses of difficulty, plausibility, and positive emotion |
| Robustness check | All models above re-estimated with participants and images as crossed random factors |

## Data

### `PORS_task.xlsx`

| Variable | Description |
|---|---|
| `Subject` | Experiencer ID (four digits, starting at 1001) |
| `Image` | Image file shown on the trial |
| `Trial` | Trial type: `Solo`, `Social`, `Look Negative`, `Look Neutral`. "Reappraisal origin" in the paper refers to `Solo` vs. `Social`. |
| `PE1` | Positive emotion after generation/receipt (or first look); 1 = *not at all*, 7 = *very positive* |
| `PE2` | Positive emotion after implementation (or second look); same scale |
| `Diff1` | Difficulty of generating or receiving the reappraisal; 0 = *did not do it*, 1 = *not at all*, 7 = *very hard* |
| `Diff2` | Difficulty of implementing the reappraisal; same scale |
| `Plau` | Plausibility of the reappraisal; 0 = *did not do it*, 1 = *not at all*, 7 = *very plausible* |
| `Success` | Implementation success; 0 = *did not do it*, 1 = *not at all*, 7 = *very successful* |
| `Tactic1`–`Tactic5` | Implementation tactics (1 = selected, 0 = not selected): focused on details in the image; added details to the image; imagined the reappraisal playing out; imagined what would happen in the future; other |

Difficulty, plausibility, success, and tactics were rated on reappraisal trials only.

### `PORS_survey.xlsx`

One row per dyad. Columns without a prefix are experiencer responses; columns prefixed `h_` are helper responses. The variables used in the analyses are:

| Variable | Description |
|---|---|
| `ID` | Experiencer ID; matches `Subject` in the task data |
| `Age`, `h_Age` | Age in years |
| `Gender`, `h_Gender` | 1 = woman, 2 = man, 3 = non-binary/non-conforming, 6 = prefer not to answer; blank = not reported |
| `Race_1`–`Race_8`, `h_Race_1`–`h_Race_8` | Race/ethnicity (1 = selected; multiple selection allowed): African American/Black; American Indian/Alaska Native; Asian/Asian American/Pacific Islander; Caucasian/European American; Middle Eastern/Arab American; Latino/Hispanic; other; prefer not to answer |
| `Support`, `Significance`, `Close`, `Trust`, `Know` | Relationship quality items (1–7), averaged into a composite |
| `Length` | Relationship length in months |

The file also contains other demographic variables and measures that were unrelated to the aims of the current study and are not analyzed in this paper.

### `PORS_hours.xlsx`

| Variable | Description |
|---|---|
| `Pair number` | Dyad number (entered on the helper row only) |
| `Role` | `Helper` or `Experiencer` |
| `ID` | Participant ID. Experiencer IDs have four digits (1001 and up); helper IDs have three digits (101 and up). |
| `Hours` | Hours per week spent with the friend outside of class |

The analyses use the experiencer's report.

## Notes for reanalysis

- Six experiencers were excluded under the preregistered criteria (IDs 1009, 1034, 1042, 1048, 1100, 1127). The script applies the exclusion criteria to the raw data, so the excluded participants remain in the data files.
- The first 21 dyads chose their own roles; later dyads were randomly assigned. The IDs of self-selected dyads are listed in the script. Role assignment did not moderate any primary finding (see the manuscript footnote).
