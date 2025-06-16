# linkdintask
Create a Codeberg repository with a simple Flask or Node.js web app (e.g., a single route displaying “Hello World”)

Set up Jenkins (on your local machine or VM)
Configure a Webhook on Codeberg to trigger a Jenkins
 pipeline on every push

The Jenkins pipeline should:
Clone or pull the latest code from Codeberg

Install dependencies
Restart the app (or redeploy using Docker if preferred)


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
       
