pipeline {
    agent any
    stages {
        stage('git clone') {
            steps {
            git url: "https://github.com/nandini965/go-node-app.git", branch: "main"
        }
        }
        stage('build,test') {
            steps {
                sh "docker build -t nandini965/node-todo-app:latest ."
            }
        }
        stage('docker run') {
            steps {
                sh "docker run -p nandini965/node-todo-app:latest"
            }
        }
    }
    }

