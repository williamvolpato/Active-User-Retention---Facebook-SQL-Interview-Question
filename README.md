# Facebook User Actions - SQL Query for Monthly Active Users (MAUs)

## Project Description
This project provides an SQL query to calculate the number of Monthly Active Users (MAUs) for Facebook user actions in July 2022. An active user is defined as someone who performed actions such as 'sign-in', 'like', or 'comment' in both the current month and the previous month.

## Table Structure
The `user_actions` table contains the following fields:
- `user_id` (integer): Unique identifier for each user.
- `event_id` (integer): Unique identifier for each event.
- `event_type` (string): Type of event (`sign-in`, `like`, `comment`, etc.).
- `event_date` (datetime): Timestamp of the event.

## Query
The query identifies active users in July 2022 who were also active in June 2022. The result includes:
- `month`: Numerical representation of the month (e.g., 7 for July).
- `monthly_active_users`: Count of distinct users.

### SQL Query:
```sql
SELECT 
  7 AS month, -- Represents July
  COUNT(DISTINCT curr_month.user_id) AS monthly_active_users
FROM user_actions AS curr_month
WHERE EXTRACT(MONTH FROM curr_month.event_date) = 7
  AND EXTRACT(YEAR FROM curr_month.event_date) = 2022
  AND EXISTS (
    SELECT 1
    FROM user_actions AS last_month
    WHERE last_month.user_id = curr_month.user_id
      AND EXTRACT(MONTH FROM last_month.event_date) = 6
      AND EXTRACT(YEAR FROM last_month.event_date) = 2022
  );
