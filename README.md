# hipages Full Stack Engineer Tech Challenge

Welcome to the hipages Data Engineer Tech Challenge! The purpose of this challenge is to help us assess your 
technical skills. We know that you have limited time to devote to this task and may not be able to provide the 
complete solution as you would if given more time, so we suggest you focus on the core requirements first, then any 
additional features if you have time left over.


## The Task
Your task is to write an ETL program to read json data and perform a series of transformations on it to build a 
structured table as result.

## Context:
- The various hipages applications send their json events to a receiver which dumps these events to disk in form of json 
lines. An example of such a file is `./source_event_data.json` in this repository, representing one event per line. 
- These events are fired on the hipages website when certain “Actions” are performed by “Users”. The file also contains 
metadata information about the url they were visiting, the time and other related information as described in this json 
schema file - `./source_data_schema.json`.

## Guide & Tips:
 
- The team is interested in the approach you follow for solving this problem
- Approach this problem as you would to build an end to end ETL pipeline.
- Keep in mind that data in production almost always has anomalies, and a robust pipeline should account for and gracefully handle such situations.
- Most of all this is your time to shine, and show us your Software engineering prowess, and to demonstrate that you approach this problem like a Data Engineer.
- You can use Java / Python / Scala.
- Think of the future iterations on your solutions and how easily it can evolve and scale
- Think about the execution environment and how portable your solution is, eg. whether you choose to build a distributed
 docker container or use a framework like Spark / Apache beam etc. Document your design choices
- We have provided some scope but if you find that it’s too broad, you are welcome to limit the scope, just let us know 
the thought process and assumptions behind your decisions
- Do not forget to add instructions for the evaluation team on how to read and execute your code
- You can use a publicly hosted version control like github.com to house the new project you are building, and send us 
this repository as your submission


## Requirements:
Your ETL program needs to consume this data and produce an output in the form of two tables (CSV):

| Field | Description | 
| --- | --- |
| user_id | identifier for the user |
| time_stamp | UTC timestamp of when the event was fired |
| url_level1 | first piece of the url (ie. the domain from the url where this action took place) |
| url_level2 | second level of the url path |
| url_level3 | third level of the url path |
| activity | activity that took place |

| Field | Description | 
| --- | --- |
| time_bucket | hourly time granularity |
| url_level1 | first piece of the url (ie. the domain from the url where this action took place) |
| activity | activity that took place |
| activity_count | count of events for the activity |
| user_count | unique number of users that performed the activity |

Example results:

| user_id | time_stamp | url_level1 | url_level2 | url_level3 | activity | 
| --- | --- | --- | --- | --- | --- | 
| 564561 | 02/02/2017 20:22:00 | hipages.com | articles | NULL | page_view | 
| 564561 | 02/02/2017 20:23:00 | hipages.com | connect | sfobusiness | button_click | 


| time_bucket | url_level1 | url_level2 | activity | activity_count | user_count |
| --- | --- | --- | --- | --- | --- |
| 2017020220 | hipages.com | articles | page_view | 4 | 1 | 
| 2017020220 | hipages.com | connect | button_click | 2 | 1 | 

Bonus:
Think of ways you can transform the source data into another format to expose other types of information. Explain why 
you chose that transformation and what types of analyses it could be used for?

