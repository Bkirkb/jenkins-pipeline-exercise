pipeline{
        agent any
        environment{
                DB_PASSWORD="password"
        }
        stages{
            stage('Make Directory for git and clone repo'){
                steps{
                    sh "mkdir ~/jenkins-exercise-repo2 || true"
                    sh "git clone https://gitlab.com/qacdevops/chaperootodo_client.git || true"
                }
            }
            stage('Install Docker and Docker Compose'){
                steps{
                    sh "curl https://get.docker.com | sudo bash"
                    sh "sudo usermod aG docker jenkins"
                    sh "sudo curl -L https://github.com/docker/compose/releases/download/1.27.4/docker-compose-\$(uname -s)-\$(uname -m) -o /usr/local/bin/docker-compose"
                    sh "sudo chmod +x /usr/local/bin/docker-compose"
                }
            }
             stage ('Deploy using docker'){
                steps{
                    sh "cd ~/jenkins-exercise-repo2 && docker-compose && docker-compose up -d"
                }
             }       
        }
     }
