pipeline {
    agent any

    stages {
        stage('clone') {
            steps {
                checkout scmGit(branches: [[name: '*/master']], extensions: [], userRemoteConfigs: [[url: 'https://github.com/Praveenchinna14/onlinebookstore.git']]) 
            }
        }
        stage('docker') {
            steps {
                script {
                     withDockerRegistry(credentialsId: 'docker-cred') {
                         sh 'docker build -t praveenchinna/candystore .'
                         sh 'docker push praveenchinna/candy:latest'
                   }
               }
            }
        }
    }
}
