pipeline {
    agent {
      dockerfile true
    }

    stages {
        stage('Build') {
            steps {
                echo 'Hello World'
                sh 'echo myCustomEnvVar = $myCustomEnvVar'
            }
        }
        stage('Test') {
            steps {
                echo 'Testing..'
            }
        }
        stage('Deploy') {
            steps {
                echo 'Deploying....'
            }
        }
    }
}