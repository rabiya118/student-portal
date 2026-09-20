pipeline {
    agent any

    triggers {
        pollSCM('H/2 * * * *')
    }

    stages {
        stage('Checkout') {
            steps {
                checkout scm
            }
        }

        stage('Build and Test') {
            steps {
                script {
                    if (isUnix()) {
                        sh 'test -f index.html && test -f styles.css'
                    } else {
                        bat 'if not exist index.html exit /b 1 && if not exist styles.css exit /b 1'
                    }
                }
            }
        }
    }
}