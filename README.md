This project is created for personal learning purpose 📖. 

It covers:
<br>🟢 Oracle Linux
<br>🟢 SQL (PostgreSQL)
<br>🟢 Docker
<br>🟢 K8s
<br>🟢 Java/Python coding
<br>🟢 AWS
<br>🟢 Jenkins
<br>🟢 Prometheus + Grafana


<br>Goal: Create a microservice application with a backend (Java Spring Boot - REST API) and a worker (Python FastAPI) 
<br>that will run Docker containers, orchastrated with K8s, deployed on AWS EKS with automated CI/CD in Jenkins.

<br> Model scenario: User management and authentication system
<br> Manage user accounts, enabling registration, login, password reset, and profile management 
<br> - user registration - username, password, and email address 
<br>                     - the backend generates a hashed password and stores it in PostgreSQL
<br>                     - the backend sends a verification email with an activation link
<br>                     - user status is set to "unverified"
<br>
<br> - user login - the user enters their username and password
<br>              - The backend verifiees the password hash
<br>              - if successful, the backend generates a JWT token for authentication
<br>
<br> - email verification - when the user clicks on the link in the email, the backend updates the status to "verified"
<br>
<br> - password reset - if the user forgets password
<br>                  - the backend generates a one-time token and sends it via email
<br> 
<br> Suspicious account detection 
<br> - FastAPI worker periodically scans the database for suspicious accounts:
<br>        - multiple failed login attempts
<br>        - multiple accounts using the same email address
<br>        - login attempts from different countries in a short time
<br>        - if suspicious pattern is detected, the worker flash the account as "flagged" and create an notification
<br>



</br>
<br>Icons: ✅- Done,🧠 -working on it, ❌ - ongoing

<br>Task_1 PostrgeSQL (docker: PSQL) ✅
<br>A) Deploy a PostgreSQL in docker ✅
<br>B) Create a database ✅
<br>C) Create simple tables  <i>credentials(id,username, password_hash, email)</i> and <i> userstat(id,username,status) </i> and <i> userlog(id,username,failed_login,geo_ip,timestamp)✅ 
<br>D) Run a test ✅

<br>Task_2 Backend (docker: java_be) 🧠
<br>A) Create a project with Java Spring Boot Framework 🧠
<br>B) Configure a connection to PostgreSQL ❌



