SQL PROJECT

MY SOLUTION 

Q1. 
with cohort_items as (
select
date_trunc('month', U.timestamp)::date as cohort_month,
id as user_id
from users U
order by 1, 2
)
WITH user_activities as (
select
A.user_id,
MONTH_DIFF(
date_trunc('month', A.timestamp)::date,
C.cohort_month
) as month_number
from public.activities A
left join cohort_items C ON A.user_id = C.user_id
group by 1, 2
)


Q2.
