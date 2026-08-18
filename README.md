# BingePlay Streaming Analytics 🎬📊

**Author:** Harshil Chauhan  
**Program:** Data Analytics & Data Science Track, The Unlox Academy  

## 📝 Project Overview
This project simulates a real-world analytics environment for **BingePlay**, a fictional Indian OTT streaming service.
Acting as the platform's first data analyst, I queried a production database of over 3,000 users and 100,000 watch sessions to answer 12 critical business questions set by the Head of Product. 

The project spans three tiers of complexity, moving from basic revenue reporting to highly advanced behavioral analytics like churn detection and gap-and-island streak calculations.

## 🛠️ Tech Stack
*   **Database:** MySQL
*   **Language:** SQL (Advanced), Python
*   **Libraries:** `pandas`, `SQLAlchemy`, `pymysql`
*   **Environment:** Jupyter Notebook

## 🔍 Key Analyses & SQL Concepts Mastered

### 1. Revenue & Subscriptions
*   Calculated total monthly recurring revenue (MRR) from active subscriptions while carefully handling open-ended (`NULL`) end dates.
*   Identified users on Premium/Family plans who exclusively consumed Basic-tier content, highlighting downgrade-risk cohorts.

### 2. User Behavior & Engagement
*   **Binge Detection:** Grouped viewing data by user, show, and specific calendar dates to isolate instances of 5+ sessions per day.
*   **Cliffhanger Comebacks:** Executed complex self-joins to find users who abandoned a session but returned to complete it within 1 to 7 days.

### 3. Advanced SQL & Edge Cases
*   **The NULL Trap (Anti-Joins):** Successfully identified inactive Q1 signups by using `LEFT JOIN` and `IS NULL` to bypass the standard evaluation failures of `NOT IN` with null data.
*   **Gaps-and-Islands (Streaks):** Solved the classic gaps-and-islands problem using `STR_TO_DATE`, interval math, and `ROW_NUMBER()` window functions to calculate 4+ week consecutive engagement streaks.
*   **Churn Signal Detection:** Built layered Common Table Expressions (CTEs) to isolate users whose watch minutes dropped by 50% or more month-over-month.

## 🗄️ Database Schema
The analysis was performed across 5 relational tables:
*   `users`: Demographics, signup dates, and referral sources.
*   `subscriptions`: Subscription history, plan tiers (Basic/Premium/Family), and active statuses.
*   `shows`: Catalog of 100 shows with IMDB ratings and tier requirements.
*   `watch_sessions`: Over 100k rows logging daily viewing behavior and completion metrics.
*   `ratings`: User-submitted 1-5 star reviews.

## 🚀 How to Run
1. Ensure MySQL is running locally.
2. Execute the provided setup script (`bingeplay_setup.sql`) to initialize the database and insert the mock data.
3. Run the `bingeplay_analytics_final.ipynb` notebook. Make sure to update the SQLAlchemy engine string with your local MySQL credentials.
