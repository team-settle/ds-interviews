Assume we have the database tables below.  Write queries to answer each of the questions.  We understand different databases have slightly different T-SQL syntax, please specify the version of SQL you are writing. It's ok for you to lookup syntax online while you work on this, but we don't expect you to spend more than 20-30 minutes total on this, please submit whatever you finish in 30 minutes.

__employees__

| id | name | start_date | end_date | department |
| --- | --- | --- | --- | --- |
| 1	| Bob	| 1/1/2018	| 3/15/2020	 | Sales |
| 2	| Alice	| 4/15/2018 |	7/20/2020 |	Engineering |
| 3	| Sue	| 5/1/2018	|	Marketing |
| 4 |	Jane	| 2/5/2019 |	Engineering |
| ... |	... |	... |	... |	... |
 

__management_relations__

| id	| manager_id	| employee_id |
| --- | --- | --- |
| 1	| 1	| 2 |
| 2	| 1	| 3 |
| 3	| 4	| 1 |
| ...	| ...	| ... |
 

__employee_reviews__

| id | employee_id | year | quarter | rating |
| --- | --- | --- | --- | --- |
| 1	| 1	| 2018	| 1	| 4 |
| 2	| 1	| 2018	| 2	| 5 |
| 3	| 2	| 2018	| 2	| 4 |
| 4	| 3	| 2018	| 2	| 3 |
| ... |	... |	... |	... |	... |


1) Show me everyone in engineering. #=> [id, name, start_date, end_date]

2) How many people *currently* work in each department? #=> [department, count]

3) Which employee has worked the longest for the company? #=> [id, name]

4) Which active employee is the longest-tenured (most time working) for each department? #=> [id, name, department]

5) What are the names of all the managers along with their team size and average employee rating given out?  #=> [manager_name, managed_employee_count, average_rating]

Note: you may find the following tool helpful for testing the output of your SQL: http://sqlfiddle.com/
If you use this tool (mysql) you can create the tables above by pasting this script in:

```SQL
create table employees (
    id serial primary key,
    name text,
    start_date date,
    end_date date,
    department text
);

insert into employees (name, start_date, end_date, department) values 
('Bob', '1/1/2018', '3/15/2020', 'Sales'),
('Alice', '4/15/2018', '7/20/2020', 'Engineering'),
('Sue', '5/1/2018', NULL, 'Marketing'),
('Jane', '2/5/2019', NULL, 'Engineering');

create table management_relations (
    id serial primary key,
    manager_id int,
    employee_id int
);

insert into management_relations (manager_id, employee_id) values 
(1,2),
(1,3),
(4,1);

create table employee_reviews (
    id serial primary key,
    employee_id int,
    year int,
    quarter int,
    rating int
);

insert into employee_reviews (employee_id, year, quarter, rating) values 
(1,2018,1,4),
(1,2018,2,5),
(2,2018,2,4),
(3,2018,2,3);
``` 
 

