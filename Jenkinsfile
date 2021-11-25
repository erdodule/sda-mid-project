pipeline {

    environment {
       registry = "erdodule/devops"
       registryCredential = 'dockerhub'
       dockerImage = ''
    }

    agent {
      dockerfile true
    }

    stages {
        stage('Build') {
            steps {
                script {
                  dockerImage = docker.build registry + ":$BUILD_NUMBER"'
                }
            }
        }
        stage('Push') {
            steps {
                script {
                  docker.withRegistry( '', registryCredential ) {
                    dockerImage.push()
                  }
                }
            }
        }
        stage('Deploy') {
            steps {
                echo 'Deploying....'
            }
        }
    }
}