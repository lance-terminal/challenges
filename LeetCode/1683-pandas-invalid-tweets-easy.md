# 1683.Pandas Invalid Tweets - Easy

| Field | Detail |
|-------|--------|
| **Issue** | [#28 - 1683.Pandas Invalid Tweets - Easy](https://github.com/lance-terminal/challenges/issues/28) |
| **Author** | @lance-terminal |
| **Labels** | LeetCode |
| **Created** | 2026-02-10T02:05:21Z |
| **Closed** | 2026-02-10T02:12:07Z |

---

# [1683. Invalid Tweets](https://leetcode.com/problems/invalid-tweets/)

Table: `Tweets`
```SQL
+----------------+---------+
| Column Name    | Type    |
+----------------+---------+
| tweet_id       | int     |
| content        | varchar |
+----------------+---------+
```
`tweet_id` is the primary key (column with unique values) for this table.
content consists of alphanumeric characters, '!', or ' ' and no other special characters.
This table contains all the tweets in a social media app.

Write a solution to find the IDs of the invalid tweets. The tweet is invalid if the number of characters used in the content of the tweet is strictly greater than `15`.

Return the result table in any order.
The result format is in the following example.

 

Example 1:

Input: 
`Tweets` table:
```SQL
+----------+-----------------------------------+
| tweet_id | content                           |
+----------+-----------------------------------+
| 1        | Let us Code                       |
| 2        | More than fifteen chars are here! |
+----------+-----------------------------------+
```
Output: 
```SQL
+----------+
| tweet_id |
+----------+
| 2        |
+----------+
```
Explanation: 
Tweet 1 has length = 11. It is a valid tweet.
Tweet 2 has length = 33. It is an invalid tweet.




## Comments

---

**lance-terminal** — 2026-02-10T02:11:34Z

```python
import pandas as pd

def invalid_tweets(tweets: pd.DataFrame) -> pd.DataFrame:
    is_valid = tweets['content'].str.len() > 15
    df = tweets[is_valid]
    return df[['tweet_id']]
```

is_valid = tweets['content'].str.len() > 15 - Creates boolean mask: True if tweet content length > 15 chars
df = tweets[is_valid] - Filters to only rows where mask is True (keeps valid tweets)
return df[['tweet_id']] - Returns just the tweet_id column as DataFrame
