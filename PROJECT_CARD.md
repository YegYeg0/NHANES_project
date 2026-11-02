# Project Card

## Dataset and scope
- **Dataset:** National Health and Nutrition Examination Survey (NHANES) — Path A
- **Cycle:** August 2021–August 2023
- **Files:** `DEMO_L.xpt`, `SLQ_L.xpt`, `PAQ_L.xpt`, `BPXO_L.xpt`, and `BMX_L.xpt`
- **Identifier for merging:** `SEQN`
- **Analytic population:** US civilian, non-institutionalized adults aged 20 years and older with complete measurements on the primary study variables ($N = 5,714$).

## Temporary title
Investigating the Association Between Lifestyle Factors (Sleep Duration and Sedentary Behavior) and Systolic Blood Pressure in US Adults, Accounting for BMI and Age

## Main statistical question
Is there a significant association between usual daily sleep duration and daily sedentary behavior (minutes spent sitting) with systolic blood pressure in US adults aged 20 and older, and how does this association change when controlling for BMI, age, and gender?

## Unit of observation and target population
- **Unit of observation:** One individual NHANES participant, uniquely identified by `SEQN` (one row per participant).
- **Target population:** Civilian, non-institutionalized US adult population (aged $\ge 20$ years) during the 2021–2023 cycle.

## Main variables and measurement scales
- `BPXOSY1` (`BPXO_L`): Systolic blood pressure, 1st oscillometric reading (mmHg) — **Quantitative, continuous**.
- `SLD012` (`SLQ_L`): Usual sleep duration on weekdays/workdays (hours) — **Quantitative, continuous**.
- `PAD680` (`PAQ_L`): Daily sedentary activity / time spent sitting (minutes/day) — **Quantitative, continuous**.
- `BMXBMI` (`BMX_L`): Body Mass Index ($\text{kg/m}^2$) — **Quantitative, continuous** (can also be categorized into standard clinical BMI groups).
- `RIDAGEYR` (`DEMO_L`): Age at screening (years, top-coded at 80) — **Quantitative, discrete**.
- `RIAGENDR` (`DEMO_L`): Gender (Male / Female) — **Categorical, binary (nominal)**.
- `WTMEC2YR` (`DEMO_L`): 2-year Mobile Examination Center (MEC) survey weight — **Sampling weight**.

## Variable roles
- **Response variable:** Systolic blood pressure (`BPXOSY1`).
- **Primary explanatory variables:** Usual sleep duration (`SLD012`) and daily sedentary activity (`PAD680`).
- **Confounding / mediating / grouping variables:** Body Mass Index (`BMXBMI`), Age (`RIDAGEYR`), and Gender (`RIAGENDR`).

## Type of question
Primarily associational and comparative.

## Initial hypothesis
Inadequate or excessive sleep duration and higher daily sedentary time are positively associated with higher systolic blood pressure among US adults, though a substantial portion of this association may be confounded or mediated by higher BMI and older age.

## Initial limitations
1. **Observational and cross-sectional design:** NHANES is not a randomized experiment; therefore, observed associations cannot establish causal relationships or temporal order.
2. **Self-reporting bias:** Sleep duration (`SLD012`) and sedentary minutes (`PAD680`) are self-reported via questionnaires and are subject to recall bias and rounding.
3. **Complete-case restriction:** Dropping participants with missing values on key variables reduces the sample size from 6,064 adults to 5,714, which may introduce selection bias if data are not missing completely at random.
