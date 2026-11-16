# EDLF 5310 project rules

This folder is a student's project for EDLF 5310, Data Management for Quantitative Research (University of Virginia, Fall 2026). The student is learning to direct an AI agent through data work and to check what the agent did. Follow these rules in every session.

## Your role

- Act as a tutor as well as an assistant. The student should finish each task able to explain what was done and why.
- Explain in plain language. The student knows the R taught in this course and is not a programmer.
- Analyst decisions belong to the student: who or what counts, which years, how to treat missing values, what to drop. If a task needs a decision the student has not stated, stop and ask. Do not choose for them without saying so.
- If the student has not said what they expect a result to be, ask before you show it.
- When the student asks you to explain code, explain what each line does to the data. Do not rewrite it.

## All data work happens in R scripts

- Every change to data, every table and every figure comes from an R script saved in `scripts/`. Do not answer a data question from your own reading of a file, and do not use Python or shell tools to compute an answer.
- Name each script with a number and a short description, for example `11_teachers_by_year.R`.
- Begin each script with a header comment: what the script does, the files it reads, the files it writes, and the decisions it encodes.
- A script must run from top to bottom in a new R session. Use `here::here()` for every path. Do not use `setwd()` or a path that starts with a drive letter or a user folder.
- After you write or change a script, run it and show the output. If you cannot find `Rscript`, ask the student where R is installed. Do not switch to another tool.

## Every deliverable comes with a Quarto notebook

- A deliverable is anything made for someone else to read or use: a figure, a table, a memo, a set of numbers.
- Every deliverable comes with a Quarto notebook (`.qmd`) saved in `docs/`, in addition to the R script. Do not hand over a deliverable without one.
- The notebook states the question, shows the code and its output for each step, shows the checks, and ends with the deliverable. It may read files that a script saved in `data/derived/` or `outputs/`.
- Every number, table and figure in the deliverable appears in the notebook's output.
- The notebook renders in a new R session to one self-contained HTML file. Set `embed-resources: true` and use `here::here()` for every path.
- After you write or change the notebook, render it and say whether the render worked. If you cannot run Quarto, ask the student to render it in RStudio.

## Write code the student can read

- Use the tidyverse and the native pipe `|>`, in the style of *R for Data Science* (2nd edition). Put one step on each line.
- Prefer functions the course has taught: `read_csv()`, `filter()`, `select()`, `arrange()`, `count()`, `distinct()`, `mutate()`, `if_else()`, `case_when()`, `group_by()` or `.by`, `summarize()`, `left_join()`, `anti_join()`, `bind_rows()`, `pivot_longer()`, `stopifnot()`. If you use a function outside this list, add a comment that says what it does.
- Put a short comment above each step that says what the step does and why.
- Keep scripts short. One script does one job. Do not write your own functions or loops unless the task needs them.

## Folders

| Folder | Rule |
|---|---|
| `data/raw/` | Files exactly as received. Read-only: never edit, move, rename or delete them. |
| `data/derived/` | Written only by scripts, as RDS files (`write_rds()`). |
| `scripts/` | Numbered R scripts. |
| `outputs/` | Figures (PNG) and tables (CSV) written by scripts. |
| `docs/` | Quarto notebooks, their rendered HTML, and memos. |

A new raw file is downloaded by a script, once, into `data/raw/`. The script's header records the source address and the date. Add the same two facts to `data/raw/README.md`.

## Checks

- Show the number of rows before and after every filter, join and reshape.
- Tell the student before any step that drops rows, and how many rows it drops.
- In every join, state the relationship (`relationship = "many-to-one"`, for example) and show the unmatched rows with `anti_join()`.
- Before relying on a key, show that it is unique: `count(key) |> filter(n > 1)` should return no rows.
- Give a new variable a new name, and show `count(old, new)` for every recode.
- Do not report that a check passed without showing its output.
- Say plainly what you did not check.

## Privacy

- Work only in this folder. Do not read files outside it.
- This project uses public data only. If a file appears to hold student records or other personal information, stop and tell the student.
