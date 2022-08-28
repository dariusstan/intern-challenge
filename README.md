* Yet Another Vulnerable Server
- Yet another vulnerable webserver (to learn XSS/SQLi/ injection).
- Written using Python3, flask, and sqlite3 library
- Relatively small code base should allow you to understand what is going on, and possibly fix vulnerabilities
- *Hints*: 
  - Most vulnerabilities had to be manually enabled, as flask prevents them by default.
  - Not much error handling, running in debug mode to allow you to see where things break
- *Disclaimer*: you should never make this server accessible to anyone except localhost. Even then, be aware it allows arbitrary command injection.

## Part 1: SQL Injection
- We run a *vulnerability_server.py* server script. 
  - Run it with python3 locally to test out your exploits
- After starting the server locally, go to http://localhost:5000 to be greeted by a login page. Alice's email is alice@alice.com, but *what is the password?*
- Find a way to log in as Alice using [SQL Injection](https://www.geeksforgeeks.org/authentication-bypass-using-sql-injection-on-login-page/)

## Part 2: Cross-Site Scripting
- Note: restarting the webserver will refresh the SQL database
** Persistent attack
- Log in as Alice again, and check the different options the website gives you. Can you use one of them to conduct a persistent XSS attack?
  - Your goal is to inject some code (HTML or .js) on a page that the admin user will look at if they search for any term. If you are not familiar with .js or HTML, you can use xss_template.html in the templates folder. 
  - In particular, assume that the admin sees a list of all news when he logs in and would search for news.
