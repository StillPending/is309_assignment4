[![License](http://img.shields.io/:license-mit-blue.svg?style=flat-square)](http://badges.mit-license.org) [![Badges](http://img.shields.io/:badges-9/9-ff6799.svg?style=flat-square)](https://github.com/badges/badgerbadgerbadger)

# Still Pending - Assignment 4
---







## Table of Contents

- [Assumptions](#assumptions)
- [Calculations](#calculations)
- [Assignment](#assignment)
- [Contribution](#team)
- [Licence](#license)





## Assumptions

We assume that I_PROJECT’s PCTFREE will be set as 25, as the assignment text only specifies that tables with little or no expansion should use the default values provided in the assignment text (1b).
Also, it is stated in the assignment that there are 267 active projects. We therefore assume that we should multiply active projects by 71 (average donations)  to find the GROWTH per Year for I_DONATION.

We assume that  INITIAL EXTENT SIZE will hold a 1-to-1 ratio with NEXT EXTENT SIZE unless NEXT EXTENT SIZE is very close to the limit.
We assume that the tables with an unknown expansion will stay as 0 expansion in the spreadsheet, in order to make the calculations easier. We remedy this by PCTFREE(value used) to either 5 or 10, depending on which table(s) the table in question has relations to.

---




## Calculations
Calculation for table growth, x being the specified base amount of items = ((x* 2) * 1.5) / 2 We round up or down when the calculations provide decimals.

[![FVCproductions](https://i.imgur.com/ywKOD86.png)](http://fvcproductions.com)

---

2. Create the necessary tablespaces. a. Write and execute the CREATE TABLESPACE command that you would use to create each of the tablespaces. NOTE!!! In your command to create a tablespace, do NOT use an extent UNIFORM SIZE larger than 4M, in spite of what you determined above. The reason is ONLY that there is limited space on the Oracle server we are using. In real life you could specify larger extent sizes. 

[![FVCproductions](https://i.imgur.com/EnnWmhw.png)](http://fvcproductions.com)

---







3. Move your i_ ioby tables into the appropriate tablespaces, with the appropriate PCTFREE, INITIAL, and NEXT extent values, as calculated above. 







4. What is the STATUS of the indexes created on the table(s) you just moved. Why
do you think that is? Move any indexes you own into the INDX tablespace.
Query the data dictionary view USER_INDEXES to see which indexes you
currently own. What is their status after you have moved them?

The status of the indexes for each table were assigned as “unusable. When we altered the indexes the status changed from “unusable” to “valid”. 

Whenever CTAS maintenance or table partition maintenance occurs, changes the indexes to  “UNUSABLE” (Donald Burleson, 2018) 
http://www.dba-oracle.com/t_indexes_invalid_unusable.htm 

PROJECT_PK	
PROJECT_TYPE_PK
WEBSITE_PK
GIVING_LEVEL_PK
FOCUS_AREA_PK
BILLING_PK
DONATION_PK
DONATION_DETAIL_PK
BUDGET_PK
ACCOUNT_PK
ACCOUNT_EMAIL_IDX
RELATION_5_PK
RELATION_3_PK

As far as we gathered, we do not own any of the LOB indexes with the sys_ prefix.


[![FVCproductions](https://i.imgur.com/nZSJDin.png)](http://fvcproductions.com)
[![FVCproductions](https://i.imgur.com/vrUW22k.pngg)](http://fvcproductions.com)



5. 5.  (Try) to create four roles such that 
a.  The first has the least possible privileges, to only read your tables.  It should not have the privileges to create anything in the database.
[![FVCproductions](https://i.imgur.com/ywKOD86.png)](http://fvcproductions.com)


We can also use a LOOP if the role should have the same privilege for all tables



b.  The second shall have the privilege to execute all of the procedures and functions in the Ioby.org3b_pkg package. 
[![FVCproductions](https://i.imgur.com/ywKOD86.png)](http://fvcproductions.com)









c.  The third should have the privilege to execute the procedures to create a new account, create a new project, create a new giving level, add a budget item to a project, and add a focus area to a project. This would be an administrative, data entry role. 
[![FVCproductions](https://i.imgur.com/ywKOD86.png)](http://fvcproductions.com)









d.  The fourth shall have the privilege to create a new account and add a donation.  This would be a donor role. 
[![FVCproductions](https://i.imgur.com/ywKOD86.png)](http://fvcproductions.com)


e.  What difficulties did you encounter in (c) and (d) in comparison to (a) and (b)?
C and D provided difficulties in comparison to A and B, mostly due to the fact that Oracle does not allow a user to grant privileges to more than one object at a time.

f.  Thought question: how can this problem be solved?  
Unfortunately, we did not find a way to solve this problem, as the documentation shows.
Theoretically, we could have created a list of tables that a function could loop through whenever we needed to work with more than one object at a time.










6. Create two users. 
a. Give the users name that start with XX_1, XX_2, where XX is the (possibly abbreviated) group name. 
[![FVCproductions](https://i.imgur.com/ywKOD86.png)](http://fvcproductions.com)       




b. Create a PROFILE with reasonable characteristics and use it when creating users. 
[![FVCproductions](https://i.imgur.com/ywKOD86.png)](http://fvcproductions.com)




c. Give all users the default tablespace USERS. 
[![FVCproductions](https://i.imgur.com/ywKOD86.png)](http://fvcproductions.com) 
 
 

This image refers to the process in done in assignment 6a, where we set the default tablespace to USERS.


d. Give user #1 a quota of 0 MB on USERS (this prevents any table creation); give user #2 a quota of 50M on USERS. 
[![FVCproductions](https://i.imgur.com/ywKOD86.png)](http://fvcproductions.com) 





e. Grant the first user role (4.a); the second user, role (4.b) 
[![FVCproductions](https://i.imgur.com/ywKOD86.png)](http://fvcproductions.com)




