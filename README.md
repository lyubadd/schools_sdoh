# Chronic School Absenteeism in NYC Public Schools
# Project Plan

## Introduction
Chronic absenteeism is the main indicator of school quality and student success that states in the U.S. have used to meet the requirements of the 2015 Every Student Succeeds Act (ESSA) governing the country’s K–12 public education policy.
In 2016 the first US Education Department report since the Act showed that more than 6 million students in the US were chronically absent, meaning they missed more than 15 school days in a year.
Six years and a pandemic later, the latest figures remain disquieting. 
Looking at New York City only, the chronic school absenteeism rate in public schools is 41%. 
This project aims to understand the underlying causes/risk factors and propose measures to address them.

## Research Questions

To understand the city’s exceptionally high school absenteeism situation, this project will answer the following research questions: 

How have the NYC chronic school absenteeism rates changed over time since the 2016-2017 school year?

Lollipop plot https://www.pluralsight.com/guides/tableau-playbook-lollipop-chart

→ need to pay special attention to the ‘interactions’ from spring 2020 (records may be unreliable)
→ account for subgroup variation (Simpson’s paradox) and intersectionality - include filters by gender/age/poverty/swd/ell

What schools and geographic areas in the city (zip code and school district) have the highest school absenteeism rates? Has the trend changed over time? If so, how? 

Maps (3 maps for school, zip code, school district)

→ How to show change over time on map https://community.tableau.com/s/question/0D54T00000C6W46SAF/map-that-changes-over-time
→ NYC zip code shapefile
https://data.cityofnewyork.us/Business/Zip-Code-Boundaries/i8iw-xf4u
→ School point locations NYC https://data.cityofnewyork.us/Education/School-Point-Locations/jfju-ynrr
→ School districts map
https://data.cityofnewyork.us/Education/School-Districts/r8nu-ymqj
→ account for subgroup variation (Simpson’s paradox) and intersectionality - include filters by gender/age/etc

What are the chronic school absenteeism neighborhood risk factors?

I wanted to practice my logistic regression skills, but I cannot think of a way of doing it on these datasets. If I had the data by individual student (anonymized) with an outcome yes/no for chronic absenteeism, I could have done it. But having the rates aggregated by school and then aggregated again by zip code, it’s just too messy and even if it makes statistical sense (which I’m not sure about), it gets too complex for my skill level. I’d rather do something simple that makes sense than do something complicated and wrong. But please let me know if you have any alternative suggestions for doing it!

So a simpler solution I could think of to show something potentially interesting would be to layer two maps on each other to see overlap between absenteeism rates and a few SDOH (e.g. digital divide, single household families, poverty rates, etc), something like this: https://help.tableau.com/current/pro/desktop/en-us/maps_dualaxis.htm

What can the city administration do to reduce the current truancy rate?

Make some recommendations based on the findings.

## Data Preparation

This project analyzes public school attendance data covering the school years between 2016 and 2022. 
As such, it represents the entire public school population in that period.
The data are first-party and are made publicly available by the NYC Department of Education on the NYC Open Data Platform (2016-2017) https://data.cityofnewyork.us/Education/2016-17-2020-21-Citywide-End-of-Year-Attendance-an/sgsi-66kk and on the NYC department of education website (2017-2022) https://infohub.nyced.org/reports/school-quality/information-and-data-overview/end-of-year-attendance-and-chronic-absenteeism-data. 
The data were analyzed in respect of applicable data privacy laws. The analysis used no students’ personally identifiable information.
The data were stored by month on the server and downloaded in xlsx files on the analyst’s personal computer.
The data are organized by [...] and cover [...] variables.
Open data platform description (to be edited):
Overall attendance data include students in Districts 1-32 and 75 (Special Education). Students in District 79 (Alternative Schools & Programs), charter schools, home schooling, and home and hospital instruction are excluded. Pre-K data do not include NYC Early Education Centers or District Pre-K Centers; therefore, Pre-K data are limited to those who attend K-12 schools that offer Pre-K. Transfer schools are included in citywide, borough, and district counts but removed from school-level files.
Attendance is attributed to the school the student attended at the time. If a student attends multiple schools in a school year, the student will contribute data towards multiple schools.
Starting in 2020-21, the NYC DOE transitioned to NYSED's definition of chronic absenteeism. Students are considered chronically absent if they have an attendance of 90 percent or less (i.e. students who are absent 10 percent or more of the total days). In order to be included in chronic absenteeism calculations, students must be enrolled for at least 10 days (regardless of whether present or absent) and must have been present for at least 1 day. The NYSED chronic absenteeism definition is applied to all prior years in the report.
School-level chronic absenteeism data reflect chronic absenteeism at a particular school. In order to eliminate double-counting students in chronic absenteeism counts, calculations at the district, borough, and citywide levels include all attendance data that contribute to the given geographic category. For example, if a student was chronically absent at one school but not at another, the student would only be counted once in the citywide calculation. For this reason, chronic absenteeism counts will not align across files.
All demographic data are based on a student's most recent record in a given year.
Students With Disabilities (SWD) data do not include Pre-K students since Pre-K students are screened for IEPs only at the parents' request.
English language learner (ELL) data do not include Pre-K students since the New York State Education Department only begins administering assessments to be identified as an ELL in Kindergarten.
Only grades PK-12 are shown, but calculations for "All Grades" also include students missing a grade level, so PK-12 may not add up to "All Grades". 
Data include students missing a gender, but are not shown due to small cell counts.
Data for Asian students include Native Hawaiian or Other Pacific Islanders . Multi-racial and Native American students, as well as students missing ethnicity/race data are included in the "Other" ethnicity category.
In order to comply with the Family Educational Rights and Privacy Act (FERPA) regulations on public reporting of education outcomes, rows with five or fewer students are suppressed, and have been replaced with an "s". Using total days of attendance as a proxy , rows with 900 or fewer total days are suppressed. In addition, other rows have been replaced with an "s" when they could reveal, through addition or subtraction, the underlying numbers that have been redacted. Chronic absenteeism values are suppressed, regardless of total days, if the number of students who contribute  at least 20 days is five or fewer. 
Due to the COVID-19 pandemic and resulting shift to remote learning in March 2020, 2019-20 attendance data was only available for September 2019 through March 13, 2020. Interactions data from the spring of 2020 are reported on a separate tab.
Interactions were reported by schools during remote learning, from April 6 2020 through June 26 2020 (a total of 57 instructional days, excluding special professional development days of June 4 and June 9). Schools were required to indicate any student from their roster that did not have an interaction on a given day. Schools were able to define interactions in a way that made sense for their students and families. Definitions of an interaction included:
• Student submission of an assignment or completion of an assessment, in whichever manner the school is collecting
• Student participation in an online forum, chat log, or discussion thread
• Student/family phone call, email or response to teacher email
• Phone, email, and/or other digital communication with a family member which confirms student interaction/engagement
• Other evidence of participation as determined by the principal.
Interactions data are attributed to students' school of record on a given day. A student participating in a Shared Instruction (SHIN) model may have recorded interactions at multiple schools on a given day, but only one record is counted for the interaction rate, attributed to students' school of record for that day.
Due to the shift to hybrid learning, attendance data for the 2020-21 school year include both in-person and remote instruction. Total days, days absent, and days present fields include both in-person and remote attendance.

## Further reading:
https://www.nyc.gov/html/truancy/downloads/pdf/attendance_presentation_nca.pdf

https://www.childtrends.org/states-missing-point-essas-fifth-indicator

https://www.npr.org/sections/ed/2016/06/10/480181439/more-than-6-million-u-s-students-are-chronically-absent

https://studentwork.prattsi.org/infovis/visualization/nyc-public-school-districts-and-locations/

https://academic.oup.com/aje/article/175/11/1133/139878?login=false

https://www.wsj.com/articles/high-rates-of-chronic-absenteeism-persist-at-u-s-schools-11672232415
