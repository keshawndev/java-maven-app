pipeline {   
    agent any
    stages {
        stage("test") {
            steps {
                script {
                    echo "Testing the application...."
                }
            }
        }
        
        stage("build") {
            steps {
                script {
                    echo "Building the application...."
                }
            }
        }

        stage("deploy") {
            steps {
                script {
                    def dockerComposeCmd = "docker-compose -f docker-compose.yaml up --detach"
                    sshagent(['ec2-server-key']){
                        sh "scp -o StrictHostKeyChecking=no docker-compose.yaml ec2-user@18.233.157.110:/home/ec2-user"
                        sh "ssh -o StrictHostKeyChecking=no ec2-user@18.233.157.110 ${dockerComposeCmd}"
                    }
                }
            }
        }               
    }
} 
