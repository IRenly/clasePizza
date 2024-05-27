pipeline {
    agent any

    environment {
        VENV = 'venv'
    }

    stages {
        stage('Checkout') {
            steps {
                git branch: 'main', url: 'https://github.com/IRenly/clasePizza'
            }
        }

        stage('Setup') {
            steps {
                bat 'python -m venv %VENV%'
                bat '.\\%VENV%\\Scripts\\pip install -r requirements.txt'
            }
        }

        stage('Test') {
            steps {
                bat '.\\%VENV%\\Scripts\\python -m unittest discover'
            }
            post {
                always {
                    junit 'test-results.xml'
                }
            }
        }

        stage('Build') {
            steps {
                bat 'echo Building the application...'
                // Aquí puedes añadir pasos adicionales de construcción si es necesario
            }
        }

        stage('Deploy') {
            steps {
                bat 'echo Deploying the application...'
                // Aquí puedes añadir pasos de despliegue si es necesario
            }
        }
    }
}
