# [SQL injection] — [SQL injection UNION attack, determining the number of columns returned by the query]

## Summary

 This lab contains a SQL injection vulnerability in the product category filter. The results from the query are returned in the application's response, so you can use a UNION attack to retrieve data from other tables. The first step of such an attack is to determine the number of columns that are being returned by the query. You will then use this technique in subsequent labs to construct the full attack.

To solve the lab, determine the number of columns returned by the query by performing a SQL injection UNION attack that returns an additional row containing null values. 


**Fix**
1. Go to the any category for e.g., Pets.
2. Malipulate the URL bar with ' UNION SELECT NULL--
3. If the page still remains the same or no changes to be found add one more NULL at the end which makes the query ' UNION SELECT NULL, NULL--
4. Repeat this until you see any error message.