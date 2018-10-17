pipeline {
    agent any
    checkout scm
    stages {
        stage('build') {
            steps {
                bat 'echo "batch build"'
                archiveArtifacts artifacts: '*.txt'
            }
            stage('Test') {
                steps {
                    copyArtifacts filter: '*.txt', fingerprintArtifacts: true, projectName: 'build', selector: lastSuccessful()
                    echo 'Testing'
                }
            }
         }
    }
}
