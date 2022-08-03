pipeline{
    agent any 
    
    stages{
        
        stage("TF Version"){
            steps{
                sh 'terraform version'
            }
        }
        stage("test"){
            steps{
                echo 'test the git and jenkins'
            }
        }
        stage("deploy"){
            steps{
                echo 'Deploy the git and jenkins'
            }
        }
    }
}
