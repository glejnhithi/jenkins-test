pipeline {
  agent {label'docker-agent-alpine'}
  environment {
    imagename = "glejnhithi/jenkins-bp"
    registryCredential = 'docker_hub'
    dockerImage = ''
  }
  stages {
    stage('Cloning Git') {
      steps {
        git branch: 'main', url:  'https://github.com/glejnhithi/jenkins-test.git' 
      }
    }
    stage('Building image') {
      steps{
        script {
          dockerImage = docker.build imagename
        }
      }
    }
    stage('Deploy Image') {
      steps{
        script {
          docker.withRegistry( '', registryCredential ) {
            dockerImage.push("$BUILD_NUMBER")
             dockerImage.push('latest')
          }
        }
      }
    }
    stage('Remove Unused docker image') {
      steps{
        sh "docker rmi $imagename:$BUILD_NUMBER"
         sh "docker rmi $imagename:latest"
 
      }
    }
  }
}
