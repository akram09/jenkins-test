 pipeline {
     agent any
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
                 sh 'docker build -t akram0907/eurecomlab:0.0.2 .'
                 sh 'docker push akram0907/eurecomlab:0.0.2'
             }
         }
     }
 }
