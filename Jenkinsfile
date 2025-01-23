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
                withCredentials([usernamePassword(
                    credentialsId:"dockerHubCreds",
                    usernameVariable:"dockerHubUser", 
                    passwordVariable:"dockerHubPass")]){
                sh 'echo $dockerHubPass | docker login -u $dockerHubUser --password-stdin'
                sh "docker image tag node-todo-app:latest ${env.dockerHubUser}/node-todo-app:latest"
                sh "docker push ${env.dockerHubUser}/node-todo-app:latest"
   
                    }
            }
        }
       
        
      }
    }

