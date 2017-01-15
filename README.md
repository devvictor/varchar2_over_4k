# varchar2_over_4k

table test_char contains following columns:
Status, reason1, reason2, reason3, other, reasonforchange
 
Status could only be active or active, not nullable. 
 
Requirement is to get status and reason for that status:
SELECT status, decode(status, 'active', reason1||reason2||reason3||other, 'inactive', reasonforchange) reason
FROM table 
 
Challenge is reason1||reason2||reason3||other could be over 4000 characters as other column is free text field defined as varchar2(4000). By concatenating all those, it would blow up the 4000 string limit. 

How could we re-wrtie the query above without encountering the issue. 
