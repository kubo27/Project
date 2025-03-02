This project is created for personal learning purpose 📖. 

It covers:
<br>🟢 Oracle Linux
🟢 SQL (PostgreSQL)
🟢 Docker
🟢 K8s
🟢 Java/Python coding
🟢 AWS
🟢 Jenkins
🟢 Prometheus + Grafana


<b>Goal: Create a microservice application with a backend (Java Spring Boot - REST API) and a worker (Python FastAPI) 
that will run Docker containers, orchastrated with K8s, deployed on AWS EKS with automated CI/CD in Jenkins. </b>

 Model scenario: User management and authentication system
 Manage user accounts, enabling registration, login, password reset, and profile management 
 - user registration - username, password, and email address 
                     - the backend generates a hashed password and stores it in PostgreSQL
                     - the backend sends a verification email with an activation link
                     - user status is set to "unverified"

 - user login - the user enters their username and password
              - The backend verifiees the password hash
              - if successful, the backend generates a JWT token for authentication

 - email verification - when the user clicks on the link in the email, the backend updates the status to "verified"

 - password reset - if the user forgets password
                  - the backend generates a one-time token and sends it via email
 
 Suspicious account detection 
 - FastAPI worker periodically scans the database for suspicious accounts:
        - multiple failed login attempts
        - multiple accounts using the same email address
        - login attempts from different countries in a short time
        - if suspicious pattern is detected, the worker flash the account as "flagged" and create an notification




</br>
<b>Icons: ✅- Done,🧠 -working on it, ❌ - ongoing </b>

<br><b>Task_1 PostrgeSQL (docker: PSQL) ✅ </b>

A) Deploy a PostgreSQL in docker ✅

B) Create a database ✅

C) Create test table ✅

D) Test connction ✅

E) Create tables via pgAdmin<i>credentials(id,username, password_hash, email)</i> and <i> userstat(username,status) </i> and <i> userlog(userlog_id,username,login_status,geo_ip,timestamp) ✅

<b>Task_2 Backend (docker: java_be) 🧠 </b>

A) Create a project with Java Spring Boot Framework 🧠

B) Configure a connection to PostgreSQL ❌

</br>


