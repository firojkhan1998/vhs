pipeline {
    agent any

    stages {

        stage('Clone Repo') {
            steps {
                git 'https://github.com/firojkhan1998/vhs.git'
            }
        }

        stage('Build Docker Image') {
            steps {
                sh 'docker build -t flask-app .'
            }
        }

        stage('Tag Image') {
            steps {
                sh 'docker tag flask-app flaskregistry123.azurecr.io/flask-app:v1'
            }
        }

        stage('Push Image') {
            steps {
                sh 'docker push flaskregistry123.azurecr.io/flask-app:v1'
            }
        }

        stage('Deploy to Kubernetes') {
            steps {
                sh 'kubectl apply -f deployment.yaml'
                sh 'kubectl apply -f service.yaml'
            }
        }
    }
}