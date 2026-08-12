pipeline{
    agent {
        label "agent-1"
    }
    stages{
        stage("Code Cloning"){
            steps{
                sh 'echo "Code Cloning"'
                git url :"https://github.com/abhishekkargeti1/CI-CD-With-Jenkins.git",branch:"main"
            }
        }
        stage("Building-JAR"){
            steps{
                sh 'echo "Code Building"'
                sh 'mvn clean package -DskipTests'
            }
        }
        stage("Building-Docker-Image"){
            steps{
                sh 'echo "Docker Image Building"'
                sh 'docker build -t authserviceimages:latest .'
            }
        }
        stage("Testing"){
            steps{
                sh 'echo "Code Testing"'
            }
        }
        stage("Pushing-Docker-Image"){
            steps{
                sh 'echo "Pushing Docker Image"'
            withCredentials([
             usernamePassword(
                 credentialsId: 'DockerCred',
                 usernameVariable: 'DOCKER_USERNAME',
                 passwordVariable: 'DOCKER_PASSWORD'
            )
        ])
                sh 'docker login -u ${env.DOCKER_USERNAME} -p ${env.DOCKER_PASSWORD}'
                sh 'docker image tag authserviceimages:latest  abhishekkargeti/authserviceimages:latest'
                sh 'docker push abhishekkargeti/authserviceimages:latest '
                sh 'echo "Image Push Successfully"'
            }
        }
        stage("Deployment"){
            steps{
                sh 'echo "Code Deployment"'
                sh 'docker stop myauthserviceapp || true' 
                sh 'docker rm myauthserviceapp || true'
                sh 'docker run -it -d --name myauthserviceapp -e DB_URL=jdbc:mysql://mysqlcontainer:3306/employee -e DB_USERNAME=${DB_USERNAME} -e DB_PASSWORD=${env.DB_PASSWORD} -p 8080:8087 --network myauthservernetwork authserviceimages:latest '
                sh 'docker image prune -f'
            }
        }
    }





}