# linkdintask
Create a Codeberg repository with a simple Flask or Node.js web app (e.g., a single route displaying “Hello World”)

Set up Jenkins (on your local machine or VM)
Configure a Webhook on Codeberg to trigger a Jenkins
 pipeline on every push

The Jenkins pipeline should:
Clone or pull the latest code from Codeberg

Install dependencies
Restart the app (or redeploy using Docker if preferred)

CI/CD Pipeline with GitHub, Jenkins, and Docker for a Python Flask App
I implemented a CI/CD pipeline for a Python Flask application using GitHub, Jenkins, and Docker.

Version Control with GitHub
The Flask application code is stored in a GitHub repository. Every change pushed to the repository serves as a trigger for the automated pipeline, ensuring continuous integration.

CI/CD Automation using Jenkins
Jenkins is configured on a virtual machine to automate the build and deployment process. A webhook connects GitHub to Jenkins, automatically triggering a Jenkins job on every code push.

Containerization with Docker
A Dockerfile is included in the project to containerize the Flask app. The Jenkins pipeline pulls the latest code, builds the Docker image, and runs the container exposing the app on a defined port.

Pipeline Workflow

Jenkins pulls code from GitHub.

Installs dependencies listed in requirements.txt.

Builds a Docker image using the Dockerfile.

Runs the container, making the Flask app accessible.

step 1: setup jenkins
Install Jenkins:
         sudo wget -O /etc/apt/keyrings/jenkins-keyring.asc \
         https://pkg.jenkins.io/debian-stable/jenkins.io-2023.key
          echo "deb [signed-by=/etc/apt/keyrings/jenkins-keyring.asc]" \
          https://pkg.jenkins.io/debian-stable binary/ | sudo tee \
  /etc/apt/sources.list.d/jenkins.list > /dev/null
          sudo apt-get update
         sudo apt-get install jenkins
  
  step2. Install Dependencies on Jenkins Server
          mkdir flask-app && cd flask-app 
          python3 -m venv venv
          source venv/bin/activate
          pip3 install Flask
step3: Sample App (app.py)---python Flask
step4: Create a Git Repository 
step5: Set Up Webhook
        Go to your repo → Settings → Webhooks → Add webhook
        URL: http://http://13.203.232.98:8080/github-webhook/
        Content type: application/json
        Select: Just the push event
step6: Freestyle Project
       Create new item → Freestyle project
       Under Source Code Management → Git
       Repo URL: https://github.com/achendel/codeberg_linkd.git
       Under Build Triggers
       Check GitHub hook trigger for GITScm polling
step7: Create Docker file for python Flask application
                                                         

  
       
