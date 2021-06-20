# Data Manipulation With R

## Why use dplyr? →

* Great for data exploration and transformation
* Fast on data frames
* Excellent for Five basic verbs: filter, select, arrange, mutate, summarise (plus group_by)

## Load dplyr

````
library(readr)
library(dplyr)
````

## Read the datasets
The four datasets we will use are:
1. questions.csv → dataset of questions asked, storing column `id` as identifier.
2. answers.csv → dataset about the answers given, column `id` as the main identifier and has column `question_id` to combine against dataset `questions`.
3. tags.csv → dataset that defines a tag/question for a particular topic.
4. question_tags.csv → dataset that assigns each question to a specific tag.

````
(questions <- read.csv("questions.csv"))
(answers <- read.csv("answers.csv"))
(question_tags <- read.csv("question_tags.csv"))
(tags <- read.csv("tags.csv"))
````

## Counting 
Count the number of question_id in the dataset answers.csv
````
answers %>% 
  count(question_id, sort = TRUE)
````

## Joining 
Join the data results to the dataset column 'questions.csv'
````
answers %>% 
  count(question_id, sort = TRUE) %>% 
  inner_join(questions, by = c("question_id" = "id"))
````

Then, join the data results to the `questions_tags.csv` dataset and to the `tags.csv` dataset
````
answers %>% 
  count(question_id, sort = TRUE) %>% 
  inner_join(questions, by = c("question_id" = "id")) %>% 
  inner_join(question_tags, by = "question_id") %>% 
  inner_join(tags, by = c("question_id" = "id"))
````

## Aggregating
Aggregate by column `tag_name` to get the number of questions that appear and sort the final result from `tag_name` most frequently.
````
answers %>% 
  count(question_id, sort = TRUE) %>% 
  inner_join(questions, by = c("question_id" = "id")) %>% 
  inner_join(question_tags, by = "question_id") %>% 
  inner_join(tags, by = c("question_id" = "id")) %>% 
  count(tag_name, sort = TRUE)
````
## Summary
In this case, we counted how many times each `question_id` appears in the `answers.csv` dataset. Joined the results to the dataset column `questions.csv`. Then, joined to dataset `questions_tags.csv` and to dataset `tags.csv`. From the result, aggregation based on column `tag_name` to get the number of times the question appears. The last sorted the final result of the `tag_name` that occurs most often.

Thank you 😁
