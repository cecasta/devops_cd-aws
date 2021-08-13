pipeline {
    agent any
    stages {
        stage ('Build') {
            steps {
                sh 'npm install'
            }
        }
        stage ('deploy') {
            steps {
                nodejs(nodeJSInstallationName: 'nodejs') {
                    withAWS(credentials: 'aws-credentials'){
                        sh 'serverless deploy'
                    }
                }
            }
        }
    }
}