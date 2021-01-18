pipeline{
        agent any
        stages{
            stage('Make Directory for git and clone repo'){
                steps{
                    sh "mkdir ~/jenkins-exercise-repo"
                    sh "git clone https://gitlab.com/qacdevops/chaperootodo_client.git"
                }
            }
            stage('Install Docker and Docker Compose'){
                steps{
                    sh "sudo apt-get update"
                    sh "curl https://get.docker.com | sudo bash"
                    sh "sudo curl -L https://github.com/docker/compose/releases/download/1.27.4/docker-compose-\$(uname -s)-\$(uname -m) -o /usr/local/bin/docker-compose"
                }
             stage ('Deploy using docker') {
                steps{
                    sh "sudo docker-compose pull && sudo -E DB_PASSWORD=\${DB_PASSWORD} docker-compose up -d
                }
             
            }
        }
     }
}
