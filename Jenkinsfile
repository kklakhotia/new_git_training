pipeline {
    agent any
    stages {
        stage('checkout') {
            steps {
                checkout scm
            }
        }
        stage('build') {
            steps {
                bat 'echo "batch build"'
                stash allowEmpty: true, includes: '*.txt', name: 'for_test'
                archiveArtifacts artifacts: '*.txt'
            }
        }
        stage('Test') {
            steps {
                unstash 'for_test'
                echo 'Testing'
            }
        }
    }
}
