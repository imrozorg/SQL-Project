

/* Q1: Check how many rows in  database. */

SELECT * From Finance_1;
SELECT * From Finance_2;


/* Q2: KPI 1 - Find Year Wise Loan Amount */

select year(issue_D) as Year_of_issue_d, sum(loan_amnt) as Total_loan_amnt
from finance_1
group by Year_of_issue_d
order by Year_of_issue_d;


/* Q3: KPI 2 - Display Grade and Sub Grade wise Revo_Bal */

select grade, sub_grade, sum(revol_bal) as total_revol_bal
from finance_1 inner join finance_2
on (finance_1.id = finance_2.id)
group by grade, sub_grade
order by grade, sub_grade;

/* Q4: KPI 3 - Toatal Payment for Verified and Non verified status? */

select verification_status,sum (total_pymnt) as total_payment
	from finance_1
	inner join finance_2 on (finance_1.id finance_2.id)
        group by verification_status;


/* KPI 4 - use round function to show only 2 decimels */

select verification_status,Round (sum (total_pymnt),2) as total_payment
	from finance_1
	inner join finance_2 on (finance_1.id finance_2.id)
        group by verification_status;


/* Q5:KPI 5 - State wise and Last_credit_pull_d wise loan status*/


select addr_State, last_Credit_pull_D, loan_Status
from finance_1 inner join finance_2 on (finance_1.id = finance_2.id)
group by addr_State, last_Credit_pull_D, loan_Status order by last_Credit_pull_D;

/* Q1: KPI 6 - homw owner ship vs last payment stats */


SELECT
home_ownership,
last_pymnt_d,
CONCAT('$', FORMAT (ROUND (SUM(last_pymnt_amnt) / 10000, 2), 2), 'K') AS total_amount
FROM
finance_1
INNER JOIN
finance_2 ON finance_1.id finance_2.id
GROUP BY
home_ownership, last_pymnt_d
ORDER BY
last_pymnt_d DESC, home_ownership DESC;

/* Q1: KPI 7 - Distince loan hoalder with total loan amount where loan is more then 100000 and loan recovery month is less then 9 months */


SELECT DISTINCT  finance_1.id.loan_holder_name, SUM(f1.loan_amount) AS total_loan_amount
FROM f1
JOIN f2 ON finance_1.id.loan_holder_id = finance_2.id.loan_holder_id
WHERE f1.loan_amount > 100000
AND f1.recovery_months < 9
GROUP BY finance_1.id.loan_holder_id, finance_2.id.loan_holder_name
HAVING SUM(f1.loan_amount) > 100000;



/* Thank You :) */
