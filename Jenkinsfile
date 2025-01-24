pipeline {
    agent any
    environment {
        MY_VAR = 'value'
        ANOTHER_VAR = 'another_value'
    }
    stages {
        stage('git clone') {
            steps {
            git url: "https://github.com/nandini965/go-node-app.git", branch: "main"
        }
        }
        stage('build,test') {
            steps {
                sh "docker build -t nandini965/node-todo-cicd:latest ."
            }
        }
        stage('docker push') {
            steps {
                echo "MY_var:${env.dockerHubUser}"
                echo "ANOTHER_VAR:${env.dockerHubPass}"
               sh 'echo $dockerHubPass | docker login -u $dockerHubUser --password-stdin'
                sh "docker push ${env.dockerHubUser}/node-todo-cicd:latest"
               
                    }
            }
        }
       
        
      }
    

