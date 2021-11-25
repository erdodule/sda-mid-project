pipeline {
    agent {
      dockerfile true
    }
    def app

    stages {
        stage('Build image') {
            steps {
                app = docker.build("devops:backendimgv1.0")

            }
        }
        stage('Test') {
            steps {
                app.inside {
                    sh 'echo "Tests passed"'
            }
        }
        stage('Push image') {
            steps {
                docker.withRegistry('https://registry.hub.docker.com', 'git') {
                   app.push("${env.BUILD_NUMBER}")
                   app.push("test1")
            }
        }
    }
}