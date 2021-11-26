pipeline{
    agent any
    environment {
        DOCKERHUB_CREDENTIALS=credentials('dockerhub')
        //KUBE_CREDENTIALS=credentials('erdokubeconfig')
        //URL=serverUrl("https://erdodns-k8s-7e4698e5.hcp.westeurope.azmk8s.io/")
    }
    stages {
        stage('Build') {
            steps {
                sh 'docker build -t erdodule/devops:backendimgv1.3 -f Dockerfile .'
            }
        }
        stage('Login') {
            steps {
                sh 'echo $DOCKERHUB_CREDENTIALS_PSW | docker login -u $DOCKERHUB_CREDENTIALS_USR --password-stdin'
            }
        }
        stage('Push') {
            steps {
                sh 'docker push erdodule/devops:backendimgv1.3'
            }
        }

         //stage('Kube apply') {
         //   steps {
         //       sh 'kubectl apply -f backend.yaml'
         //   }
         // }

        stage ('kube'){
            steps {
                 //withKubeCredentials([kubectlCredentials: 'KUBE_CREDENTIALS', serverUrl: 'URL']){
                    sh ("/usr/local/bin/kubectl -n jenkins apply -f backend.yaml")
            }
        }
    }
    post {
        always {
            sh 'docker logout'
        }
    }
}