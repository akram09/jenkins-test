 pipeline {
     agent any
     environment {
         DOCKER_CREDENTIALS = credentials('dockerhub-credentials') // Use the ID of your credentials
     }
     stages {
         stage('Lint') {
             steps {
		 sh '''
		 #!/bin/bash
		 python3 -m venv venv
                 . ./venv/bin/activate
                 pip install flake8
                 flake8 app.py
		 '''
             }
         }
         stage('Format') {
             steps {
		 sh '''
		 #!/bin/bash
		 python3 -m venv venv
                 . ./venv/bin/activate
                 pip install black
                 black --check app.py
		 '''
             }
         }
         stage('Build') {
             steps {
		 sh 'whoami'
		 sh 'echo $DOCKER_CREDENTIALS_PSW | docker login -u $DOCKER_CREDENTIALS_USR --password-stdin'
                 sh 'docker build -t akram0907/eurecomlab:0.0.2 .'
                 sh 'docker push akram0907/eurecomlab:0.0.2'
             }
         }
     }
 }
