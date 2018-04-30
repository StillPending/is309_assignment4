[![License](http://img.shields.io/:license-mit-blue.svg?style=flat-square)](http://badges.mit-license.org) [![Badges](http://img.shields.io/:badges-9/9-ff6799.svg?style=flat-square)](https://github.com/badges/badgerbadgerbadger)

# Still Pending - Assignment 4
---







## Table of Contents

- [Assumptions](#assumptions)
- [Calculations](#calculations)
- [Assignment](#assignment)
- [Contribution](#contribution)





## Assumptions

We assume that I_PROJECT’s PCTFREE will be set as 25, as the assignment text only specifies that tables with little or no expansion should use the default values provided in the assignment text (1b).
Also, it is stated in the assignment that there are 267 active projects. We therefore assume that we should multiply active projects by 71 (average donations)  to find the GROWTH per Year for I_DONATION.

We assume that  INITIAL EXTENT SIZE will hold a 1-to-1 ratio with NEXT EXTENT SIZE unless NEXT EXTENT SIZE is very close to the limit.
We assume that the tables with an unknown expansion will stay as 0 expansion in the spreadsheet, in order to make the calculations easier. We remedy this by PCTFREE(value used) to either 5 or 10, depending on which table(s) the table in question has relations to.

---




## Calculations
Calculation for table growth, x being the specified base amount of items = ((x* 2) * 1.5) / 2 We round up or down when the calculations provide decimals.

[![Calculations](https://i.imgur.com/ywKOD86.png)](http://i.imgur.com/ywKOD86)


---

## Assignment

---

**2. Create the necessary tablespaces. a. Write and execute the CREATE TABLESPACE command that you would use to create each of the tablespaces. NOTE!!! In your command to create a tablespace, do NOT use an extent UNIFORM SIZE larger than 4M, in spite of what you determined above. The reason is ONLY that there is limited space on the Oracle server we are using. In real life you could specify larger extent sizes.**

[![Calculations](https://i.imgur.com/EnnWmhw.png)](http://i.imgur.com/EnnWmhw)

---







**3. Move your i_ ioby tables into the appropriate tablespaces, with the appropriate PCTFREE, INITIAL, and NEXT extent values, as calculated above.**

[![Calculations](https://i.imgur.com/XwNegFP.png)](http://i.imgur.com/XwNegFP)

---




**4. What is the STATUS of the indexes created on the table(s) you just moved. Why
do you think that is? Move any indexes you own into the INDX tablespace.
Query the data dictionary view USER_INDEXES to see which indexes you
currently own. What is their status after you have moved them?**

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


[![Calculations](https://i.imgur.com/nZSJDin.png)](http://i.imgur.com/nZSJDin)

[![Calculations](https://i.imgur.com/ARCBQjr.png)](http://i.imgur.com/ARCBQjr)


---

**5. (Try) to create four roles such that**
**a.  The first has the least possible privileges, to only read your tables.  It should not have the privileges to create anything in the database.**


[![Calculations](https://i.imgur.com/smpkEaA.png)](https://i.imgur.com/smpkEaA)


We can also use a LOOP if the role should have the same privilege for all tables

[![Calculations](https://i.imgur.com/qfEtq3h.png)](http://i.imgur.com/qfEtq3h)


---

**b.  The second shall have the privilege to execute all of the procedures and functions in the Ioby.org3b_pkg package.**


[![Calculations](https://i.imgur.com/DXlEBOQ.png)](http://i.imgur.com/DXlEBOQ)


---





**c.  The third should have the privilege to execute the procedures to create a new account, create a new project, create a new giving level, add a budget item to a project, and add a focus area to a project. This would be an administrative, data entry role.**


[![Calculations](https://i.imgur.com/DGQMtJR.png)](http://i.imgur.com/DGQMtJR)

[![Calculations](https://i.imgur.com/5VyqEmi.png)](http://i.imgur.com/5VyqEmi)

[![Calculations](https://i.imgur.com/IhUCTVa.png)](http://i.imgur.com/IhUCTVa)

---







**d.  The fourth shall have the privilege to create a new account and add a donation.  This would be a donor role.**

[![Calculations](https://i.imgur.com/vm41yOn.png)](http://i.imgur.com/vm41yOn)

---

**e.  What difficulties did you encounter in (c) and (d) in comparison to (a) and (b)?**

C and D provided difficulties in comparison to A and B, mostly due to the fact that Oracle does not allow a user to grant privileges to more than one object at a time.

---

**f.  Thought question: how can this problem be solved?**

Unfortunately, we did not find a way to solve this problem, as the documentation shows.
Theoretically, we could have created a list of tables that a function could loop through whenever we needed to work with more than one object at a time.

---



**6. Create two users.**
**a. Give the users name that start with XX_1, XX_2, where XX is the (possibly abbreviated) group name.**

[![Calculations](https://i.imgur.com/LWVgszF.png)](http://i.imgur.com/LWVgszF)

[![Calculations](https://i.imgur.com/UpYcvY8.png)](http://i.imgur.com/UpYcvY8)

---


**b. Create a PROFILE with reasonable characteristics and use it when creating users.**

[![Calculations](https://i.imgur.com/Oqo9r3e.png)](http://i.imgur.com/Oqo9r3e)

---


**c. Give all users the default tablespace USERS.**

[![Calculations](https://i.imgur.com/MPPjWGc.png)](http://i.imgur.com/MPPjWGc)

This image refers to the process in done in assignment 6a, where we set the default tablespace to USERS.

---




**d. Give user #1 a quota of 0 MB on USERS (this prevents any table creation); give user #2 a quota of 50M on USERS.**

[![Calculations](https://i.imgur.com/Gegy64J.png)](http://i.imgur.com/Gegy64J)

[![Calculations](https://i.imgur.com/wT36SQ1.png)](http://i.imgur.com/wT36SQ1)


---




**e. Grant the first user role (4.a); the second user, role (4.b)**

[![Calculations](https://i.imgur.com/vm41yOn.png)](http://i.imgur.com/vm41yOn)

---

## Contribution

Ali Al-Musawi 

Eirik Fintland 

Peter Kwasa 

Osman Younas

---



