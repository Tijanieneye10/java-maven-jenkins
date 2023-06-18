pipeline {
    agent any
    tools {
        maven 'maven3.9'
    }

    stages {
        stage("build jar") {
            steps {
                echo "building the application..."
                sh "mvn package"
            }
        }

        stage("build image"){
            steps {
                script{
                    echo "building the docker image..."
                    withCredentials([
                        usernamePassword(credentialsId: 'DockerHub', passwordVariable: 'PASSWORD', usernameVariable: 'USERNAME' )
                    ]){
                        sh 'docker build -t brainydeveloper/maven:1.2 .'
                        sh "echo $PASSWORD | docker login -u $USERNAME --password-stdin"
                        sh 'docker push brainydeveloper/maven:1.2'
                    }   
                }
              
            }
        }

        stage("deploy"){
            steps {
                script {
                 echo "Wow application deployed"
                }
               
            }
        }
    }
}