pipeline {
    agent any

    environment {
        VENV = 'venv'
    }

    stages {
        stage('Checkout') {
            steps {
                git 'https://github.com/IRenly/clasePizza'
            }
        }

        stage('Setup') {
            steps {
                sh 'python3 -m venv $VENV'
                sh './$VENV/bin/pip install -r requirements.txt'
            }
        }

        stage('Test') {
            steps {
                sh './$VENV/bin/python -m unittest discover'
            }
            post {
                always {
                    junit 'test-results.xml'
                }
            }
        }

        stage('Build') {
            steps {
                sh 'echo "Building the application..."'
                // Aquí puedes añadir pasos adicionales de construcción si es necesario
            }
        }

        stage('Deploy') {
            steps {
                sh 'echo "Deploying the application..."'
                // Aquí puedes añadir pasos de despliegue si es necesario
            }
        }
    }
}

