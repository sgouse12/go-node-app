pipeline {
    agent any
    stages {
        stage('docker') {
            steps {
                sh 'docker build -t nandini965/node-todo-app:latest'
            }
            steps {
                sh 'docker run -p nandini965/node-todo-app:latest'
            }
        }
    }
}
