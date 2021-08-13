pipeline {
    agent any
    stages {
        stage ('Build sin test') {
            steps {
                nodejs(nodeJSInstallationName: 'nodejs') {
                    sh 'npm install'
                    sh 'npm rebuild'
                    sh 'npm run build --skip-test --if-present'
                }
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