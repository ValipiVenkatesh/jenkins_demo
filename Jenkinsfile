pipeline {
    agent any

    stages {
        stage('Build Docker Image') {
            steps {
                echo 'building docker image'
                
                sh('docker build -t tirumalanithya123/nithyaimage .')
            }
        }
        
        
        stage('Publish to Dockerhub') {
            steps {             
                
                sh('docker login -u tirumalanithya123 -p nithya@123')
                
                sh('docker push tirumalanithya123/nithyaimage')
                
                echo 'pushed image to docker hub'
            }
        }
        
        
        stage('pull image from Dockerhub') {
            steps {
                
                sh('docker pull tirumalanithya123/nithyaimage')
                
                echo 'pulled image from Dockerhub'
                
                sh('docker images')
                
                echo 'Displayed previous images && pulled image' 
            }
        }
        
        
        stage('start a container') {
            steps {
                sh '''if [ $(docker ps | awk \'{print $NF}\' | grep nithya-jenkins-container123) = \'-nithya-jenkins-container123\' ]; then
                        docker stop "nithya-jenkins-container123"
                        docker rm "nithya-jenkins-container123"
                      fi'''
               
                sh('docker run -it -d -p 8081:80 --name nithya-jenkins-container123 tirumalanithya123/nithyaimage')
                
                sh('docker exec nithya-jenkins-container123 service nginx start')
                
            }
        }
    }
}
