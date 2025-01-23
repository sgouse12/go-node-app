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
                sh "docker run -p 8000:8000 -it nandini965/node-todo-app:latest"
            }
        }
        stage('Deploy our image') {
         steps {
               docker.withRegistry('https://registry.hub.docker.com', 'git') {  
                docker run -p 8000:8000("latest")
                docker push("latest")
              }
         }
        }
      }
    }

