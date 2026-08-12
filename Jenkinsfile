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
        stage("Deployment"){
            steps{
                sh 'echo "Code Deployment"'
                sh 'docker run -it -d --name myauthservicecontainer -e DB_URL=jdbc:mysql://mysqlcontainer:3306/employees -e DB_USERNAME=root -e DB_PASSWORD=1808 -p 8080:8080 --network myauthservernetwork authserviceimages:latest '
            }
        }
    }





}