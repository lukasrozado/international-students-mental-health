
# Mental Health Analysis of International Students

This project explores whether studying in a foreign country affects students' mental health. A Japanese international university conducted a survey in 2018, and the data was published in a 2019 study approved by ethical and regulatory boards.

The study concluded that international students face a higher risk of mental health difficulties compared to the general population. It also found that:
- **Social connectedness** (belonging to a group) and 
- **Acculturative stress** (stress from adapting to a new culture) 

are both predictors of **depression**.

## Objective

Use PostgreSQL to analyze mental health indicators among international students, and determine:
- If the findings of the original study hold true
- Whether the **length of stay** impacts mental health

## Dataset: `students`

| Field Name     | Description                                           |
|----------------|-------------------------------------------------------|
| `inter_dom`    | Type of student (`Inter` for international)           |
| `japanese_cate`| Japanese language proficiency                         |
| `english_cate` | English language proficiency                          |
| `academic`     | Current academic level (undergraduate or graduate)    |
| `age`          | Age of student                                        |
| `stay`         | Length of stay in years                               |
| `todep`        | Depression score (PHQ-9 test)                         |
| `tosc`         | Social connectedness score (SCS test)                |
| `toas`         | Acculturative stress score (ASISS test)              |

## Example SQL Query

This query checks average mental health scores among international students based on length of stay:

```sql
SELECT
    stay,
    COUNT(*) AS count_int,
    ROUND(AVG(todep), 2) AS average_phq,
    ROUND(AVG(tosc), 2) AS average_scs,
    ROUND(AVG(toas), 2) AS average_as
FROM
    students
WHERE
    inter_dom = 'Inter'
GROUP BY
    stay
ORDER BY
    stay DESC
LIMIT 9;
```

## Goal

Explore patterns and correlations in mental health metrics to better understand the challenges international students may face, and how duration of stay could influence these factors.
