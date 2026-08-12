pipeline{
    agent {
        label "agent-1"
    }
    stages{
        stage{
            steps("Code Cloning"){
                sh 'echo "Code Cloning"'
                git url :"https://github.com/abhishekkargeti1/CI-CD-With-Jenkins.git",branch:"main"
            }
        }
        stage{
            steps("Building"){
                sh 'echo "Code Building"'
            }
        }
        stage{
            steps("Testing"){
                sh 'echo "Code Testing"'
            }
        }
        stage{
            steps("Deployment"){
                sh 'echo "Code Deployment"'
            }
        }
    }





}