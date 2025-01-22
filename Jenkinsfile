 pipeline {
     agent any
     stages {
         stage('Lint') {
             steps {
		 sh 'python3 -m venv venv'
                 sh 'source venv/bin/activate'
                 sh 'pip install flake8'
                 sh 'flake8 app.py'
             }
         }
         stage('Format') {
             steps {
		 sh 'python3 -m venv venv'
                 sh 'source venv/bin/activate'
                 sh 'pip install flake8'
                 sh 'black --check app.py'
             }
         }
         stage('Build') {
             steps {
                 sh 'docker build -t <dockerhub-username>/<repo-name>:0.0.1 .'
                 sh 'docker push <dockerhub-username>/<repo-name>:0.0.1'
             }
         }
     }
 }
