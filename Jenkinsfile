pipeline {
    agent any
    environment {
        doc_cred = credentials ('dockerhub')
    }
    stages {
        stage ('Copy From GIT') {
            steps {
                git credentialsId: 'Github', url: 'https://github.com/vinodmvd/vinodmvd.github.io.git'
            }
        }
        stage ('BUILD DOC IMAGE') {
            steps {
                sh 'docker build . -t vinodmur/myportfolio'
            }
        }
        stage ('PUSH DOC IMAGE') {
            steps{
                sh 'docker login -u ${doc_cred_USR} -p ${doc_cred_PSW}'
                sh 'docker push vinodmur/myportfolio'
            }
        }
    }
}
