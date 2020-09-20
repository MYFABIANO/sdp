--------------------
Assignment 5: Software Design - UML Design Description Document
--------------------
Mingfeng Qian 
mqian30@gatech.edu

--------------------
Requirement:
--------------------
When the app is started, the user is presented with the main menu, which allows the user to (1) enter current job details, (2) enter job offers, (3) adjust the comparison settings, or (4) compare job offers (disabled if no job offers were entered yet).  


--------------------
Design:
--------------------
The MainMenu class represents the entry point to the system, and that ties the various pieces together. The class has four operations that allows users to access to the four screens abovementioned.

--------------------
Requirement:
--------------------
When choosing to enter current job details, a user will:
Be shown a user interface to enter (if it is the first time) or edit all of the details of their current job, which consist of:
Title
Company
Location (entered as city and state)
Overall cost of living in the location (expressed as an index)
Commute time (round-trip and measured in hours or fraction thereof)
Yearly salary
Yearly bonus
Retirement benefits (as percentage matched)
Leave time (vacation days and holiday and/or sick leave, as a single overall number of days)
Be able to either save the job details or cancel and exit without saving, returning in both cases to the main menu.

--------------------
Design:
--------------------
This is realize in the JobInfo class. The list of items is attributes of the class. Users can input their own job information in these attributes. The save, cancel, exit and return to main menus are operations of the class, by using which users can decide how to treat their input.

--------------------
Requirement:
--------------------
When choosing to enter job offers, a user will:
Be shown a user interface to enter all of the details of the offer, which are the same ones listed above for the current job.
Be able to either save the job offer details or cancel.
Be able to (1) enter another offer, (2) return to the main menu, or (3) compare the offer with the current job details (if present).

--------------------
Design:
--------------------
This is realized in the EnterJobOffers class. The class inherits the JobInfo class. In addition, it allows users to accomplish the required actions by using additional operations such as :
<br/>-enterAnotherJob(): enter another offer
<br/>-returnToMain(): return to the main menu
<br/>-compareJob(): compare the offer with the current job details (if present). . 

--------------------
Requirement:
--------------------
When adjusting the comparison settings, the user can assign integer weights to:
Commute time
Yearly salary
Yearly bonus
Retirement benefits
Leave time
If no weights are assigned, all factors are considered equal.

--------------------
Design:
--------------------
This is realized in the class ComparisonSetting. The weights are stored in the attributes.

--------------------
Requirement:
--------------------
When choosing to compare job offers, a user will:
Be shown a list of job offers, displayed as Title and Company, ranked from best to worst (see below for details), and including the current job (if present), clearly indicated.
Select two jobs to compare and trigger the comparison.
Be shown a table comparing the two jobs, displaying, for each job:
Title
Company
Location
Commute time
Yearly salary adjusted for cost of living
Yearly bonus adjusted for cost of living
Retirement benefits (as percentage matched)
Leave time
Be offered to perform another comparison or go back to the main menu.

--------------------
Design:
--------------------
<br/>This is realized in the CompareJobOffer class. 
<br/>The class will be extracting all job information stored in the back-end database and display title and company in the frontend.
<br/>User can select two job offers by using the operations selectTwoJobs(), return to main menu by using returnToMain(), and create another comparison by using anotherComparison(). 
<br/>Once the user selects two jobs, the user will be displayed a table with the data for the two selected jobs as comparison.

--------------------
Requirement:
--------------------
When ranking jobs, a job’s score is computed as the weighted sum of:

AYS + AYB + (RBP * AYS) + (LT * AYS / 260) - (CT * AYS / 8)

where:

AYS = yearly salary adjusted for cost of living
AYB = yearly bonus adjusted for cost of living
RBP = retirement benefits percentage
LT = leave time
CT = commute time
The rationale for the CT subformula is:
value of an employee hour = (AYS / 260) / 8
commute hours per year = CT * 260
therefore commute-time cost = CT * 260 * (AYS / 260) / 8 = CT * AYS / 8

For example, if the weights are 2 for the yearly salary, 2 for the retirement benefits, and 1 for all other factors, the score would be computed as:
2/7 * AYS + 1/7 * AYB + 2/7 * (RBP * AYS) + 1/7 * (LT * AYS / 260) - 1/7 (CT * AYS / 8)

--------------------
Design:
--------------------
This is not represented in my design, as it will be handled entirely within the database implementation.


--------------------
Requirement:
--------------------
The user interface must be intuitive and responsive.

--------------------
Design:
--------------------
This is not represented in my design, as it will be handled entirely within the GUI implementation.


--------------------
Requirement:
--------------------
The performance of the app should be such that users do not experience any considerable lag between their actions and the response of the app.

--------------------
Design:
--------------------
This is not represented in my design, as it will be handled entirely within the app infrastructure and database implementation.


