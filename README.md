# GitHub-Actions-CICD-Pipeline-Python-App

## Description

This project demonstrates the implementation of a CI/CD pipeline using GitHub Actions for a Python application. The pipeline automates the processes of testing, building, and deploying the application to ensure seamless integration and delivery.

<br />

---

## Project Workflow

1. **Code Commit:** Developers push code to the GitHub repository.
2. **Automated Testing:** GitHub Actions runs unit tests to validate the application's functionality.
3. **Build Process:** The pipeline builds the application into a deployable format.
4. **Deployment:** The built application is deployed to the desired environment (e.g., a server, container, or cloud platform).

### **Pipeline Structure**

| **Stage**           | **Purpose**                                                                 |
|----------------------|-----------------------------------------------------------------------------|
| **Checkout**         | Fetches the latest code from the repository.                               |
| **Set Up Environment** | Installs dependencies and sets up the Python environment.                |
| **Unit Tests**       | Executes automated tests to verify application functionality.              |
| **Build**            | Packages the application for deployment.                                  |
| **Deploy**           | Deploys the application to the target environment.                        |

---

## Prerequisites

1. **GitHub Repository:** A repository containing the Python application code.
2. **Configured GitHub Actions:** Enable GitHub Actions in the repository settings.
3. **Secrets Management:** Add necessary secrets for deployment, such as API keys or environment variables.
4. **Python Version:** Ensure the desired Python version is specified in the configuration.


## Step 1: Create the main.yml and app.py files

<br/> Navigate to the .github/workflows section create/copy the listed files <br/> 

<img src="https://github.com/user-attachments/assets/72a5aa44-67ea-435d-b430-532221420689"/>
<br/> The pipline will begin but we will see it has failed since the DockerHub account and password has not been defined <br/> 
<img src="https://github.com/user-attachments/assets/7a81903d-4c0b-413d-87ac-b8e57b152494"/>



## Step 2: Define the DockerHub account user name and password 

<br/> Go to Secrets and Variables within GitHub  to configure the <br/> 

<img src=""/>


