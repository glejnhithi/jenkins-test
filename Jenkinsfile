<<<<<<< HEAD
node {
    def app

    stage('Clone repository') {
        /* Let's make sure we have the repository cloned to our workspace */

        checkout scm
=======
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
>>>>>>> b5931cd5d4467ec1c91866f34558f801a148580d
    }

    stage('Build image') {
        /* This builds the actual image; synonymous to
         * docker build on the command line */

        app = docker.build("glejnhithi/jenkins_bp")
    }

    stage('Test image') {
        /* Ideally, we would run a test framework against our image.
         * For this example, we're using a Volkswagen-type approach ;-) */

        app.inside {
            sh 'echo "Tests passed"'
        }
    }

    stage('Push image') {
        /* Finally, we'll push the image with two tags:
         * First, the incremental build number from Jenkins
         * Second, the 'latest' tag.
         * Pushing multiple tags is cheap, as all the layers are reused. */
        docker.withRegistry('https://registry.hub.docker.com', 'docker_hub') {
            app.push("${env.BUILD_NUMBER}")
            app.push("latest")
        }
    }
<<<<<<< HEAD
}
=======
    stage('Remove Unused docker image') {
      steps{
        sh "docker rmi $imagename:$BUILD_NUMBER"
         sh "docker rmi $imagename:latest"
 
      }
    }
  }
}
>>>>>>> b5931cd5d4467ec1c91866f34558f801a148580d
