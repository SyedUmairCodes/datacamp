# Student Mental Health Project

## Project Information

Does going to university in a different country affect your mental health? A Japanese international university surveyed its students in 2018 and published a study the following year that was approved by several ethical and regulatory boards.

The study found that international students have a higher risk of mental health difficulties than the general population, and that social connectedness (belonging to a social group) and acculturative stress (stress associated with joining a new culture) are predictive of depression.

Explore the `students` data using PostgreSQL to find out if you would come to a similar conclusion for international students and see if the length of stay is a contributing factor.

Here is a data description of the columns you may find helpful.

| Field Name      | Description                                        |
| --------------- | -------------------------------------------------- |
| `inter_dom`     | Types of students (international or domestic)      |
| `japanese_cate` | Japanese language proficiency                      |
| `english_cate`  | English language proficiency                       |
| `academic`      | Current academic level (undergraduate or graduate) |
| `age`           | Current age of student                             |
| `stay`          | Current length of stay in years                    |
| `todep`         | Total score of depression (PHQ-9 test)             |
| `tosc`          | Total score of social connectedness (SCS test)     |
| `toas`          | Total score of acculturative stress (ASISS test)   |

## Solution

First, list all of the data in the students table to get a better understanding of the table.

```sql
-- Run this code to view the data in students
SELECT * 
FROM students;
```

Create a query based on the requirements given in the project's instructions.

```sql
SELECT stay, 
       COUNT(*) AS count_int, 
       ROUND(AVG(todep), 2) AS average_phq,
       ROUND(AVG(tosc),2) AS average_scs, 
       ROUND(AVG(toas),2) AS average_as
FROM students
WHERE inter_dom = 'Inter'
GROUP BY stay
ORDER BY stay DESC;
```
