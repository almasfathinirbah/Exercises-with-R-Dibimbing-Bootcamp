# Data Manipulation With R

The four datasets we used are:
* questions.csv → dataset of questions asked, storing column `id` as identifier.
* answers.csv → dataset about the answers given, column `id` as the main identifier and has column `question_id` to combine against dataset `questions`.
* tags.csv → dataset that defines a tag/question for a particular topic.
* question_tags.csv → dataset that assigns each question to a specific tag.

## Summary
In this case, we counted how many times each `question_id` appears in the `answers.csv` dataset. Joined the results to the dataset column `questions.csv`. Then, joined to dataset `questions_tags.csv` and to dataset `tags.csv`. From the result, aggregation based on column `tag_name` to get the number of times the question appears. The last sorted the final result of the `tag_name` that occurs most often.

Thank you 😁
