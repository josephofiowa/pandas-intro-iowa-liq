<!--
---
title: Pandas II
type: lesson
duration: "0:45"
creator: Joseph Nelson
Private gist location: xxxxxx
Presentation URL: xxxxx
---
-->

## ![](https://ga-dash.s3.amazonaws.com/production/assets/logo-9f88ae6c9c3871690e33280fcf557f33.png) Pandas II

## Overview
The goal of this lesson is to continue demonstrating valuable functions within the Pandas library for exploratory data analysis.

This lesson includes slides and a notebook. To present this content, it is recommended you begin directly with the Jupyter Notebook. Note that the student slides contain the wrap-up of the big ideas covered in the notebook.


## Important Notes or Prerequisites

- Review the Iowa liquor dataset [here](https://data.iowa.gov/Economy/Iowa-Liquor-Sales/m3tr-qhgy)
- Be aware that the dataset you are examining is a **subset** of that dataset: it is only May 2017 and May 2018. **New columns** have been created to delineate: `is_may_2017` and `is_may_2018`. These are demonstrated for the purposes of showing filters.
- There are **Class Questions** littered throughout the notebook. Use as much/little time on these as you see fit relative to how your class is pacing


---

## Learning Objectives
*After this lesson, you will be able to:*

*After this lesson, you will be able to:*

- Identify and handle missing values with Pandas.
- Implement groupby statements for specific segmented analysis.
- Use apply functions to clean data with Pandas.



## Duration
45 minutes.

---

## Suggested Agenda

|    Time     | Activity | Purpose |
|-------------|----------|---------|
| 0:00 - 0:02 | Reintroduce Pandas | Remember Pandas! |
| 0:02 - 0:05 | Reintroduce Dataset | Walkthrough Iowa Liquor Data Dictionary - Note Modifications |
| 0:05 - 0:10 | Read in Dataset | Read in the Data, Rename Columns (Review) |
| 0:10 - 0:25 | Handling Missing Data | Identify Missing Data, and How to Fill It in |
| 0:25 - 0:35 | Groupby Statements | Introduce and Demonstrate Groupby |
| 0:35 - 0:45 | Apply Functions | Demonstrate Using Apply Functions |



## Differentiation and Extensions

- If students are excelling in the first half, consider deeper discussions surrounding types of missingness (missing at random, missing conditionally at random, not missing at random). Also, write a few more `groupby` statements.
- If students are struggling, hone the conceptual elements of each portion heavily - the **why** for identifying and handling missing data, groupby, and apply functions. Note that the order of these lessons is in order of importance, so even if the latter half is rushed, students will be covering the major keys!

---

## Lesson Procedure
<!--- This section outlines the lesson plan with relevant sections and subsections, providing both the total time required as well as suggestions for timing in each subsection. -->

---

## Reintroduce Pandas (2 minutes)

**Teaching Tips:**

- Show how common it is to check `df.head()` throughout the EDA process.

---

## Reintroduce Dataset (3 minutes)

**Teaching Tips:**

- Note that we have modified the dataset to make it <100MB, and interesting for student use.
- You may, again, walkthrough the dataset directly on the Iowa gov't [page](https://data.iowa.gov/Economy/Iowa-Liquor-Sales/m3tr-qhgy).


**Talking Points:**

- This is the same dataset as the last lesson, minimizing time lost due to context switching. 

Remember the last lesson talking points here:

- The raw dataset itself is nearly 4GB, so we have trimmed the dataset to be *just* May 2017 and May 2018. Your RAM is welcome!
- The State of Iowa may be most interested in incoming tax revenue, and predicting how much to expect
- A prospective liquor store owner may be interested in seeing top selling areas in the state -- but using a separate (not included) dataset on population to identify regions where per capita consumption is high, yet liquor supply is comparatively low. Moreover, liquor store owners may care most about bottles sales compared to bottle retail prices (all in the dataset!)

---

## Read in the Data (5 minutes)

**Teaching Tips**

- Straightforward `pd.read_csv()`!
- Note we use a special encoding - this is because we are reading in a file that has been formatted a specific way in Excel. Tell students this is non-essential for many CSVs.

**Talking Points**

- Just like last time, we are going to rename our columns to make them more intuitive, and easier to work with.

---

## Handling Missing Data (15 minutes)

**Teaching Tips**

This part of the lesson starts with identifying missing data, and then transitions into different ways to handle missing data (dropping or how to fill in).

At this stage, **emphasize** there is not a single solution for missing data, and it depends on the context under which data is missing.

When we do `dropna()` in this portion, we are not dropping the values inplace. (This is noted in the notebook.)

(Note: We are creating our own missing data, randomly, in the first part of this section. You may zip through this and simply let students know each one of them is randomly eliminating observations for the purpose of our lesson)

**Talking Points**

- Missing data is all about context: We need to understand what data is missing, and if there is a *pattern* to those missing observations. 
- Missing data ruins the quality of our insights: Without a fair sample, we cannot draw fair conclusions

To handle missing data,

We may:

- Delete missing data altogether
- Fill in missing data with:
    - The average of the column
    - The median of the column
    - A predicted amount based on other factors
- Collect more data:
    - Resample the population
    - Followup with the authority providing data that is missing

- In our case, we determine the missing data should be filled in with median rather than mean. **If the column of interest is skewed, median is generally a better choice** given it will not fall victim to outliers as heavily as mean.

---

## Groupby Statements (15 minutes)

**Teaching Tips**

- Emphasize 'split, apply, combine' as a means to understanding groupby statements. "Apply and combine" often happen concurrently.

## ![](http://i.imgur.com/yjNkiwL.png)


**Talking Points**

- Groupby are an immensely useful way to conduct specific analysis on a subset of the population
- Remember we can aggregate in multiple ways at once

---

## Apply Functions (10 minutes)

**Teaching Tips**

- Walkthrough the apply function *as if you care about one specific value* at a time
- If students are excelling, allow them to write and create their own apply functions in this section.

**Talking Points**

- Apply functions are "the for loop of Pandas." If you are writing a for loop with Pandas, chances are you are writing inefficient code!
- Think about apply functions in relation to their execution on **a single value**, and we're feeding single values one-by-one across a whole series.

---


