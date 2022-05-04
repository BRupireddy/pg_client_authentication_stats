# pg_client_authentication_stats

A PostgreSQL extension to provide client authentication stats such as number of successful or failed connection attempts, IP addresses or host names, number of total logins, SSL/GSS authentication types etc. As of this writing, it makes more sense to write all of these info into an extension's table (say pg_client_authentication_info or pg_client_auth_info) which gets created/dropped as part of CREATE/DROP EXTENSION with the proper permissions to it for security reasons (as the login information may contain ip addresses or host names, SSL or GSS info etc.).

NOTE: This extension is under development.
