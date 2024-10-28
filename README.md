# HR Projects and Department Analysis
## Project Overview
The primary goal of this personal project is to help manage the workforce, understand financial risks, monitor project health more effectively. The company also wanted to  improve workforce management, optimize resources, and align HR efforts with organizational goals.
## Data Sources
HR Project and Department Dataset: The primary dataset used for this analysis is from a youtuber named `Absent Data` where you can find the data [here](https://absentdata.com/data-analysis/data-analysis-end-to-end-project/), containing detailed information about each data made by the company. 

## Tools
- SQL Server Management Studio - Data Cleaning and Data Analysis
- Microsoft PowerBI - Dashboards and Reporting

### Data Cleaning/Preparation
In the inital data preparation phase, I performed the following tasks:
1. Data loading and inspection
2. Handling missing values
3. Data cleaning and formatting
4. Creating Database

### Exploratory Data Analysis
EDA involved exploring the HR project and department information to answer the following key questions such as:

1. Which projects and departments are at risk of being over budget or under performing? `Note that department budgets are set at 2-year intervals. We want to know if a year can cover all expenses.`
2. Identify departments and projects in red.
3. Ensure that data from various sources `e.g employee information, salary data, department budgets, and project details` is structured correctly and accessible for reporting.
4. Collaborate with us to create a comprehensive dashboard that provides visibility into employee performance, salary distribution and department project management.

### Data Analysis
```sql
with project_status as (
select 
project_id,
project_name,
project_budget,
'upcoming' as status
from [upcoming projects]
union all
select 
project_id,
project_name,
project_budget,
'completed' as status
from completed_projects)

-- big table
select
e.employee_id,
e.first_name,
e.last_name,
e.job_title,
e.salary,
d.Department_Name,
pa.project_id,
project_name,
p.status
from employees e
join departments d
on e.department_id = d.Department_ID
join project_assignments pa
on pa.employee_id = e.employee_id
join project_status p
on p.project_id = pa.project_id 
```

### Data Visualization
In this phase, I created the comprehensive dashboard to highlight the project overview and gain insights from the Exploratory Data Analysis.

![Data Project 2](https://github.com/user-attachments/assets/7ed1804d-7cd3-4da3-ab22-14d68884ec14)


By using Microsoft PowerBi, I utilized different tools such as stack bar chart, slicer, donut chart and table to showcase the visual of the data made from the query from SQL. 
In this section I want to showcase my learnings on how I manipulate the visuals on PowerBI, on how important SQL query is in trasnferring to visualization.


![Data Project 2 1](https://github.com/user-attachments/assets/b911d7c4-3f36-42ed-ba07-ec85cc30a449)


Here are some examples and my learnings on how I created this Dashboard:

1. Using donut chart, with combination of table and slicer type of visual, I arrive into visual where I can sort, select, and filter by Department Name on slicer, `status` if completed or not, department goals, project cost, salary cost, budget, 2-year budget and capital using table.
   In this part of visual, you can also figure out which department is under performing.
   
![Data Project 2 3](https://github.com/user-attachments/assets/6a5c5d73-3a47-4bed-b177-a76c3190a364)

2. Another visual type I learned is through making sort & select on employee ID and filter their name, job title, Department name, and compensation using the card and slicer visual.
   In this part of visual, employer can select on what statistics they want to command and filter based on what data they need. I showcase that we can sort employees ID no, with their snapshot and information.

![Data Project 2 5](https://github.com/user-attachments/assets/cefc989a-0ca7-4316-9bd2-2c635256da0d)


### Results/Findings:

The analysis resuslts are summarized as follows:

1. Project Distribution and Capital Overview:

`Capital`:

- $1.288M total, with breakdowns by departments (highlighted in the left donut chart).
Largest capital share: IT (26.32%) with $150K, followed closely by Engineering (19.3%) and Marketing (20.18%).
This indicates that IT and Engineering are resource-intensive areas, aligning with their focus on infrastructure and product development.

`Project Budget`:

Total allocated budget for these projects: $205K.
The chart on the right provides clarity on how individual projects are allocated within this budget.

2. Department Goals Table:
   
`Human Resources (HR)`:

HR shows negative capital of -25K, indicating it is over budget.
Immediate action: HR needs budget realignment or reallocation from other departments (such as Engineering, which holds a surplus of $770K).

`IT Department`:

Limited capital of $58K, signaling the need for careful monitoring to prevent future deficits.
Suggestion: Consider spreading IT-related tasks across multiple phases to reduce pressure on this year’s budget.

`Engineering and Marketing`:

These departments hold significant reserves ($770K and $369K).
Ensure that these surpluses don't result from delayed milestones or underutilized resources.

3. Employee and Department Filters:
   
`Employee Profile Example`:

Liam Brown, Software Engineer in Engineering, with a compensation of $85K.
This employee-level view allows HR and managers to drill down into specific staff performance, costs, and department contributions.

`Filter Controls`:

Users can filter by department or project status (e.g., completed).
This enables quick insights into current and completed initiatives.

4. Project Budgets Section:
   
`Project Breakdown`:

Example projects such as Product Launch ($80K) and Brand Repositioning ($70K) have the highest allocations.
Recommendation: Review projects with lower spend (like Customer Support and Website Overhaul) to ensure no bottlenecks are causing underperformance.

`Project Budgets by Department`:

- Sales: Leads with a project allocation of $150K.
- Other departments such as Marketing and IT show moderate project budgets.\
- Suggestion: Monitor Sales closely to ensure return on investment for these high-budget initiatives.


### Recommendations:

1. Address Budget Deficits in HR:
- Investigate why HR has overspent and assess whether any funds can be reallocated from Engineering or Marketing.

2. Monitor IT Expenses:
- Keep a close watch on IT spending, given its tight budget of $58K in capital reserves.

3. Optimize Dashboard Usage:
- Train department heads to leverage the filters (e.g., by status or employee) for granular insights.
  Set alerts for projects or departments nearing their budget limits to prevent overspending.

4. Track Underutilized Projects:
- Investigate low-priority or underfunded projects like the Website Overhaul to prevent delays from affecting future goals.


### References:

1. https://absentdata.com/data-analysis/data-analysis-end-to-end-project/
2. https://www.youtube.com/@absentdata


OCTOBER 2024

Prepared and Analyzed by:

Reinnance Rafael S. Javin

Data Analyst & Registered Mechanical Engineer 💻



   








