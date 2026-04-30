🟢 Easy — Single table or simple JOIN

1. List all active members along with their branch name and city.
2. How many members does each branch have?
3. Which membership plans exist, ordered by price from cheapest to most expensive?
4. List all trainers and their specialization, sorted by branch.
5. How many equipment items (total quantity) does each branch have?
6. List all classes scheduled at each branch.
7. Which members were born before 1980 and are still active?

🟡 Medium — Multi-table JOINs, GROUP BY, filtering

1. How many completed personal training sessions has each trainer conducted?
2. Which members have never booked a single class? (LEFT JOIN + NULL check)
3. What is the total amount paid by each member, sorted highest to lowest?
4. Which class has the highest number of attended bookings across all branches?
5. List members whose membership has expired but their status is still active. (data integrity check)
6. How many in-person vs. virtual sessions has each trainer conducted?
7. Which branch generates the most revenue from payments?
8. List all members who have held more than one membership plan over time.

🟠 Hard — Subqueries, CTEs, window functions, date logic

1. What is the month-over-month revenue trend per branch? (DATE_TRUNC + window or GROUP BY)
2. Find members who have an active membership but have never attended any class or training session — completely inactive users.
3. Which trainer has the highest no-show rate (no_shows / total sessions)? (CASE + ROUND + GROUP BY)
4. For each branch, what is the average number of days a member stays before going inactive or leaving?
5. Rank members by total spend within their branch using a window function. (RANK() OVER PARTITION BY)
6. Find the most popular membership plan per branch — the one most members are currently subscribed to.
7. What is the churn rate per month — members who left vs. members who joined in the same month?
