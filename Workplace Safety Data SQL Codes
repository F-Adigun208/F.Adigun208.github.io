--Question 1: How many incidents occurred at each plant?

SELECT Plant
,COUNT(INCIDENT_TYPE) as NO_OF_INCIDENTS
FROM[dbo].[CSV_Workplace DATA]
GROUP BY Plant

OR

SELECT*
,COUNT(INCIDENT_TYPE) OVER(Partition by Plant) as NO_OF_INCIDENTS 
FROM [dbo].[CSV_Workplace DATA]

--Question 2: What is the total incident cost per department?

SELECT Department
,SUM(incident_cost) as total_incident_cost
FROM [dbo].[CSV_Workplace DATA]
GROUP BY Department

OR

SELECT*
,SUM(INCIDENT_COST) OVER(Partition by Department) as total_incident_cost
FROM [dbo].[CSV_Workplace DATA]

--Question 3: Which incident type resulted in the highest total days lost?

SELECT incident_type
,sum(Days_lost) total_Days_lost
FROM[dbo].[CSV_Workplace DATA]
GROUP BY Incident_type

OR

SELECT*
,SUM(Days_lost) OVER(Partition by Incident_type) as total_Days_lost
FROM[dbo].[CSV_Workplace DATA]

--Question 4: What is the distribution of incident types by shift?

SELECT Shift, Incident_Type
,COUNT(INCIDENT_TYPE) Distr_incident_TYpe
FROM[dbo].[CSV_Workplace DATA]
GROUP BY Shift, Incident_Type

--Question 5: What is the average incident cost for each injury location?

SELECT Injury_location
,AVG(Incident_cost) Avg_inc_cost
FROM[dbo].[CSV_Workplace DATA]
GROUP BY Injury_Location

OR

SELECT*
,AVG(Incident_cost) OVER(Partition by Injury_location) Avg_inc_cost
FROM[dbo].[CSV_Workplace DATA]

--Question 6: Which age group has the highest number of incidents?

SELECT Age_group
,COUNT(Incident_type) highest_no_of_incident
FROM[dbo].[CSV_Workplace DATA]
GROUP BY Age_group

OR 

SELECT*
,COUNT(Incident_type) OVER(Partition by Age_group) highest_no_of_incident
FROM[dbo].[CSV_Workplace DATA]

--Question 7: How many incidents were reported as 'Lost Time' by each plant?

SELECT Plant
,Count(report_type) no_of_lost_time
FROM[dbo].[CSV_Workplace DATA]
WHERE Report_Type='Lost Time'
GROUP BY Plant

OR 

SELECT*
,COUNT(REPORT_TYPE) OVER(PARTITION BY Plant) 
from[dbo].[CSV_Workplace DATA]
WHERE Report_TYPE='LOST TIME'

--Question 8: Which department had the highest number of 'Crush & Pinch' incidents?

SELECT Department 
,COUNT(Incident_type)
FROM[dbo].[CSV_Workplace DATA]
WHERE INCIDENT_TYPE='Crush & Pinch'
GROUP BY Department

OR

SELECT*
,COUNT(INCIDENT_TYPE) OVER(Partition by Department) AS HIGHEST_CRUSH_PINCH
FROM[dbo].[CSV_Workplace DATA]
WHERE Incident_Type='Crush & Pinch'

--Question 9: Which plants reported the most "Near Miss" incidents?

SELECT Plant
,count(report_type) Most_near_miss
from[dbo].[CSV_Workplace DATA]
WHERE REPORT_TYPE='Near Miss'
GROUP BY Plant

OR

SELECT*
,COUNT(REPORT_TYPE) OVER(Partition by Plant)
FROM[dbo].[CSV_Workplace DATA]
WHERE REPORT_TYPE='Near Miss'

--Question 10: What is the total number of incidents by year and month?

SELECT Month,Year
,COUNT(incident_type)
FROM[dbo].[CSV_Workplace DATA]
GROUP BY Month,Year

OR 

SELECT*
,COUNT(INCIDENT_TYPE) OVER(Partition by Month, Year) INCident_by_M_Y
FROM[dbo].[CSV_Workplace DATA]

--Question 11: Which gender has the most reported incidents?

Select Gender
,COUNT(Incident_type)
FROM[dbo].[CSV_Workplace DATA]
GROUP BY Gender

OR

SELECT*
,COUNT(Incident_type) OVER(Partition by Gender) INCIDENT_BY_GENDER
FROM[dbo].[CSV_Workplace DATA]

--Question 12: What is the total cost of incidents per year?

SELECT YEAR
,SUM(INCIDENT_COST)
FROM[dbo].[CSV_Workplace DATA]
GROUP BY Year

OR

SELECT*
,SUM(Incident_COST) OVER(Partition by Year) Annual_incid_cost
FROM[dbo].[CSV_Workplace DATA]

--Question 13: Which incident resulted in the highest cost?

WITH CTE AS(

SELECT incident_type
,SUM(Incident_cost) AS high_cost_inc
FROM[dbo].[CSV_Workplace DATA]
GROUP BY Incident_Type
)

SELECT TOP 1 *
FROM CTE

--Question 14: What is the total cost of incidents for each report type?

SELECT REPORT_TYPE
,SUM(Incident_cost)
FROM[dbo].[CSV_Workplace DATA]
GROUP BY Report_Type

OR 

SELECT*
,SUM(Incident_cost) OVER(Partition by Report_type) COST_PER_REport_type
FROM[dbo].[CSV_Workplace DATA]

--Question 15: Which departments had incidents with more than 2 days lost?

SELECT Department,Days_Lost
FROM[dbo].[CSV_Workplace DATA]
WHERE Days_Lost>'2'
GRoup by Department, Days_Lost

--Question 16: What is the average number of days lost per incident type?

SELECT Incident_type
,AVG(Days_Lost) AVG_Days_lost
from[dbo].[CSV_Workplace DATA]
GROUP BY incident_type

OR 

SELECT*
,AVG(Days_lost) OVER(Partition by Incident_type) AVG_Days_lost
FROM[dbo].[CSV_Workplace DATA]

--Question 17: What is the distribution of incidents by shift (Day, Afternoon, Night)?

SELECT Shift
,count(incident_type)
FROM[dbo].[CSV_Workplace DATA]
GROUP BY Shift

--Question 18: Which months have the highest number of incidents?

WITH CTE AS(

SELECT Month
,COUNT(Incident_type) nUMBER_OF_Incidents
FROM[dbo].[CSV_Workplace DATA]
GROUP BY Month
)

SELECT Top 5 *
FROM CTE

--Question 19: What is the total cost of "Vehicle" related incidents?

SELECT Incident_type
,sum(incident_COST) TOT_Cost_of_v
from[dbo].[CSV_Workplace DATA]
WHERE Incident_type='vehicle'
GROUP BY Incident_Type

--Question 20: Which age group is most affected by "Falling Object" incidents?

SELECT age_group
,count(incident_type)as Falling_obj
FROM [dbo].[CSV_Workplace DATA] 
WHERE Incident_Type='Falling object'
GROUP BY Age_Group
ORDER BY Falling_obj DESC
