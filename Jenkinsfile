pipeline {
    agent none
    options {
        buildDiscarder(logRotator(numToKeepStr: '5'))
    }
    environment {
        DOCKERHUB_CREDENTIALS = credentials('dockerhub')
    }

    stages {
        stage('Build') {
            steps {
                script {
                    node {
                        sh 'docker build -t khadija915/dodo:latest .'
                        sh 'echo $DOCKERHUB_CREDENTIALS_PSW | docker login -u $DOCKERHUB_CREDENTIALS_USR --password-stdin'
                        sh 'docker push khadija915/dodo:latest'
                    }
                }
            }
        }
    }
}
