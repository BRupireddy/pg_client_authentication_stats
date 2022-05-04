# pg_client_authentication_stats

A PostgreSQL extension to provide client authentication stats (by implementing ClientAuthentication_hook) such as number of successful or failed connection attempts, IP addresses or host names, number of total logins, SSL/GSS authentication types etc. As of this writing, it makes more sense to write all of these info into an extension's table (say pg_client_authentication_info or pg_client_auth_info) which gets created/dropped as part of CREATE/DROP EXTENSION with the proper permissions to it for security reasons (as the login information may contain ip addresses or host names, SSL or GSS info etc.).

Also, writing to a table might bloat the database if there are many clients connecting to server which is quite possible in production environments. One can think of auto-loading the tables rows (say after every 1000 rows or some pre-configured number of rows) to a file (using COPY command) and delete the rows, but this isn't an elegant design IMO.

An alternative is to write the stats to a file under user-specified directory (may be as a csv file so that it can be loaded to a table using COPY command to do further analysis).

NOTE: This extension is under development.
