pipeline {
    agent any

    stages {
        stage('Build Docker Image') {
            steps {
                echo 'building docker image'
                
                sh('docker build -t tnithya123/nithya-docker-jenkins-image . ')
            }
        }
        
        
        stage('Publish to Dockerhub') {
            steps {             
                
                sh('docker login -u tnithya123 -p PRETTY@per$i$t')
                
                sh('docker push tnithya123/nithya-docker-jenkins-image')
                
                echo 'pushed image to docker hub'
            }
        }
        
        
        stage('pull image from Dockerhub') {
            steps {
                
                sh('docker pull tnithya123/nithya-docker-jenkins-image')
                
                echo 'pulled image from Dockerhub'
                
                sh('docker images')
                
                echo 'Displayed previous images && pulled image' 
            }
        }
        
        
        stage('start a container') {
            steps {
                sh '''if [ $(docker ps | awk \'{print $NF}\' | grep nithya-jenkins-container123) = \'-nithya-container123\' ]; then
                        docker stop "nithya-jenkins-container123"
                        docker rm "nithya-jenkins-container123"
                      fi'''
               
                sh('docker run -it -d -p 8084:80 --name nithya-jenkins-container123 tnithya123/nithya-docker-jenkins-image')
                
                sh('docker exec nithya-jenkins-container123 service nginx start')
                
            }
        }
    }
}
