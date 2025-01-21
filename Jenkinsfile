pipeline {
    agent any
    stages {
        stage('Lint') {
            steps {
                sh 'flake8 app.py'
            }
        }
        stage('Format') {
            steps {
                sh 'black --check app.py'
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
