--> Note: Queries are structured to progressively explore relationships between role, experience, and industry.

# SQL Queries Used in Salary Analysis Project

This document contains the SQL queries used to analyse how job role, experience, and industry influence salary.

---

## 1. Initial Data Exploration

Retrieve sample data to understand the structure:

SELECT TOP 10 *
FROM dbo.job_salary_prediction_dataset;

---

## 2. Salary by Job Role

Analyse average salary across different roles:

SELECT 
    job_title,
    AVG(salary) AS avg_salary,
    MIN(salary) AS min_salary,
    MAX(salary) AS max_salary
FROM dbo.job_salary_prediction_dataset
GROUP BY job_title
ORDER BY avg_salary DESC;

---

## 3. Salary vs Experience

Understand how salary changes with experience:

SELECT 
    experience_years,
    AVG(salary) AS avg_salary
FROM dbo.job_salary_prediction_dataset
GROUP BY experience_years
ORDER BY experience_years;

---

## 4. Role Comparison (India Focus)

Compare salaries for roles within India:

SELECT 
    job_title,
    AVG(salary) AS avg_salary,
    AVG(experience_years) AS avg_experience
FROM dbo.job_salary_prediction_dataset
WHERE location = 'India'
GROUP BY job_title
ORDER BY avg_salary DESC;

---

## 5. Experience Distribution by Role

Check experience range for each role:

SELECT 
    job_title,
    MIN(experience_years) AS min_exp,
    MAX(experience_years) AS max_exp,
    AVG(experience_years) AS avg_exp
FROM dbo.job_salary_prediction_dataset
WHERE location = 'India'
GROUP BY job_title;

---

## 6. Industry-wise Analysis (Data Analyst)

SELECT 
    industry,
    COUNT(*) AS total_jobs,
    AVG(salary) AS avg_salary,
    MAX(salary) AS max_salary,
    AVG(experience_years) AS avg_experience
FROM dbo.job_salary_prediction_dataset
WHERE job_title = 'Data Analyst'
GROUP BY industry
ORDER BY avg_salary DESC;

---

## 7. Industry-wise Analysis (Data Scientist)

SELECT 
    industry,
    COUNT(*) AS total_jobs,
    AVG(salary) AS avg_salary,
    MAX(salary) AS max_salary,
    AVG(experience_years) AS avg_experience
FROM dbo.job_salary_prediction_dataset
WHERE job_title = 'Data Scientist'
GROUP BY industry
ORDER BY avg_salary DESC;

---

## 8. Combined Role + Experience Analysis

SELECT 
    job_title,
    experience_years,
    AVG(salary) AS avg_salary
FROM dbo.job_salary_prediction_dataset
WHERE location = 'India'
GROUP BY job_title, experience_years
ORDER BY job_title, experience_years;
