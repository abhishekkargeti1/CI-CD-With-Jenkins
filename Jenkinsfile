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
        stage("Building"){
            steps{
                sh 'echo "Code Building"'
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
            }
        }
    }





}