<!--
---
title: Intro Pandas I
type: lesson
duration: "1:00"
creator: Joseph Nelson
Private gist location: xxxxxx
Presentation URL: xxxxx
---
-->

## ![](https://ga-dash.s3.amazonaws.com/production/assets/logo-9f88ae6c9c3871690e33280fcf557f33.png) Pandas I

## Overview
The goal of this lesson is to introduce the Pandas library, and the beginnings of Exploratory Data Analysis. The majority of the lesson should be spent going through code -- whether that is via Jupyter Slides or a Jupyter Notebook demonstration.

To present this content, begin with `02-pandas-i.md` to introduce Pandas as a library and data integrity. Transition to the Jupyter Notebook to introduce reading in data, column manipulation, filtering and sorting, and conclude with exercises.


## Important Notes or Prerequisites

- Review the Iowa liquor dataset [here](https://data.iowa.gov/Economy/Iowa-Liquor-Sales/m3tr-qhgy)
- Be aware that the dataset you are examining is a **subset** of that dataset: it is only May 2017 and May 2018. **New columns** have been created to delineate: `is_may_2017` and `is_may_2018`. These are demonstrated for the purposes of showing filters.
- There are **Class Questions** littered throughout the notebook. Use as much/little time on these as you see fit relative to how your class is pacing
- There is an **Independent Exercise** at the end of this lesson. It is aspirational to have time to let students work entirely independently on this time-wise, so consider doing a guided code-along or paired programming. Answers are included.


---

## Learning Objectives
*After this lesson, you will be able to:*

*After this lesson, you will be able to:*

- Use Pandas to read in a dataset.
- Investigate a dataset's integrity.
- Filter, sort, and manipulate DataFrame series.


## Duration
60 minutes.

---

## Suggested Agenda

|    Time     | Activity | Purpose |
|-------------|----------|---------|
| 0:00 - 0:02 | What is Pandas | Introduce the Pandas library conceptually |
| 0:02 - 0:05 | What is EDA | Describe Exploratory Data Analysis |
| 0:05 - 0:10 | What is the Dataset | Introduce the Dataset and Corresponding Data Dictionary |
| 0:10 - 0:15 | What is Data Integrity | Describe Data Integrity as an Ongoing Process |
| 0:15 - 0:15 | **CODE** | Open Code, or Jupyter Slides |
| 0:15 - 0:25 | Basic Pandas | Read in Data, Demonstrate Fundamental Methods/Attributes of `DataFrame` |
| 0:25 - 0:30 | Selecting/Renaming Columns | Select/Rename Columns with Pandas |
| 0:30 - 0:35 | Notable Column Operations | Show Unique Values and Value Counts |
| 0:35 - 0:45 | Filtering and Sorting | Introduce Boolean Filtering and Descending Sorting |
| 0:45 - 0:55 | Independent Exercise | Student Practice |
| 0:55 - 0:60 | Independent Exercise Shareout | Review Student Answers |


## Differentiation and Extensions

- If students are excelling in the first half, consider deeper discussions surrounding five number summaries, data integrity, off-the-cuff filters and sorts
- If students are struggling, work on the code more heavily than the **Class Questions** portions. Make the Independent Exercises be Collective Exercises (as a class)

---

## Lesson Procedure
<!--- This section outlines the lesson plan with relevant sections and subsections, providing both the total time required as well as suggestions for timing in each subsection. -->

---

## What is Pandas (2 minutes)

**Teaching Tips:**

- Reinforce the value of libraries
- Show your favorite Pandas gifs [Seriously](https://media.giphy.com/media/z6xE1olZ5YP4I/giphy.gif)

**Talking Points:**

Pandas is one of the most useful data manipulation libraries. Its utilities, on the outset, replace many things we know how to do in Excel. However, we also produce a script for creating reproducible steps **and** Excel is limited to 1.3M rows. Pandas is not.

---

## What is EDA (3 minutes)

**Teaching Tips:**

- Describe exploratory data analysis as an **ongoing** process, and cite an example from your experience.

**Talking Points:**

It's common to get later in the data science workflow, only to realize unclean data or a feature could be engineered earlier in the process. 

Hypothesis-driven EDA is essential to productive EDA -- otherwise we will ceaselessly torture our data for answers.

---

## What is the Dataset (5 minutes)

**Teaching Tips:**

- Encourage students to conceptualize how they could use the dataset from the State of Iowa's perspective as well as a prospective liquor store owner. This invests students in potential conclusions from EDA.
- Walkthrough the dataset directly on the Iowa gov't [page](https://data.iowa.gov/Economy/Iowa-Liquor-Sales/m3tr-qhgy).

**Talking Points:**

- The raw dataset itself is nearly 4GB, so we have trimmed the dataset to be *just* May 2017 and May 2018. Your RAM is welcome!
- The State of Iowa may be most interested in incoming tax revenue, and predicting how much to expect
- A prospective liquor store owner may be interested in seeing top selling areas in the state -- but using a separate (not included) dataset on population to identify regions where per capita consumption is high, yet liquor supply is comparatively low. Moreover, liquor store owners may care most about bottles sales compared to bottle retail prices (all in the dataset!)


---

## What is Data Integrity (5 minutes)

**Teaching Tips**

- Put a student in a hypothetical position where they are totally missing a fair sample (e.g. a presidential poll that only dials men). How would this affect our outcomes? This shows the value of fair samples. 

**Talking Points**

- Like EDA, data integrity checks are an ongoing process
- Consider playing a 'game' demonstrating three numbers' changing mean v median: [5,10,15] then [5,10,150] then [5,10,1500] to demonstrate the impact skews have on our process.

---

## Basic Pandas  (10 minutes)

**Teaching Tips**

- Do not spend too much time discussing reading in data - there is plenty to cover
- However, **do** open up the `pd.read_csv` documentation and walkthrough a couple of arguments. Showing students documentation is their friend early on is essential to building strong programmers.

**Talking Points**

- Discuss the difference between methods and attributes, and relate this back to object oriented programming. Show how `head()` has parentheses, but `shape` does not and why methods that take arguments are different than attributes, which are features of an object
- Deliberately show the importance and **incongruencies** in datatypes. Discuss why Pandas intepreted price values to be objects (strings) rather than numbers, and how this will impact the operations we can perform. For example, we cannot easily call the mean of a string -- but we are certainly interested in the mean price. (This is an issue we will address in Pandas II)

---

## Selecting/Renaming Columns (5 minutes)

**Teaching Tips**

- Show why the `inplace=True` argument exists. It is conceptually challenging, but important to call out
- Encourage students to think about more efficient (programmatic) ways to replace spaces with underscores (e.g. producing a function that converts spaces to underscores and applying it to our existing column names)


**Talking Points**

- It's common to have a targeted list of columns in mind in advance of conducting EDA - those that make most sense for the context of our dataset
- Show how we use `head()` after our changes to confirm our process succeeded.

---

## Notable Column Operations (5 minutes)

**Teaching Tips**

- If students are progressing quickly, demonstrate how we can pass different arguments to `describe()` to more effectively describe various datatypes of interest
- Connect the 'five number summary' to skewed samples previously discussed when introducing data integrity

**Talking Points**

- **Skew** exists when we have a mean that is dramatically larger or smaller than our median. If the mean is much larger, we may have positive outliers; the opposite is true for a small mean vs median. This impacts the quality of our analysis given our observations are wrapped by a narrow, vocal minority of data points
- Show how we can use string splicing (specifically with `value_counts()`) to connect back to earlier lessons on strings

---

## Filtering and Sorting (10 minutes)

**Teaching Tips**

- **Go slowly** as you introduce the idea of a Boolean filter. Demonstrate we create a series of `True` and `False` values. We then use that series as an *index* on our DataFrame - just like `df['column']`.
- Walkthrough (as the notebook does) how we turn a large problem into much smaller ones when finding the average pack size.
- Call out `Ascending = False` when we're filtering our DataFrame


**Talking Points**

- Boolean Filters require that we align our Boolean Series filter with the index of our original DataFrame
- Boolean Filters are like the "pivot tables" of Pandas (though we can make pivot tables too)
- We can lace together operations -- filtering, sorting and indexing -- to produce powerful conclusions with the very little code we already know!

---

## Independent Exercises (And Solutions) (15 minutes)

**Teaching Tips**

- Give students the opportunity to work in pairs, if necessary
- Encourage students to revisit previous code when they are stuck
- Circulate the room throughout the exercise
- Call on students to share that you **know did not get the answer** to demonstrate you will work with someone, even when they are concerned they're not getting it (this is key to a healthy class overall!)
- Answers are provided in a separate notebook with "answers" appended to the name


