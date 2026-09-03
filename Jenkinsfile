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
                    def dockerCmd = "docker run -p 3080:3080 -d kbarbary211/react-nodejs-example:latest"
                    sshagent(['ec2-server-key']){
                        sh "ssh -o StrictHostKeyChecking=no ec2-user@18.233.157.110 ${dockerCmd}"
                    }
                }
            }
        }               
    }
} 
