pipeline {
    agent any
    
    stages {
        stage('Checkout') {
            steps {
                checkout scm
            }
        }
        
        stage('Build') {
            steps {
                script {
                    sh 'pip install -r requirements.txt'
                }
            }
        }
        
        stage('Run') {
            steps {
                script {
                    sh 'python src/main.py'
                }
            }
        }
        
        stage('Test') {
            steps {
                script {
                    sh 'python -m unittest discover tests'
                }
            }
            post {
                always {
                    junit 'test-reports/*.xml'
                }
            }
        }
    }
}

