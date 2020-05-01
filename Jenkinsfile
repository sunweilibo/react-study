pipeline {
    agent any
    stages {
        stage('build') {
            steps {
                sh 'npm --version'
                sh 'echo "hello world"'
                sh '''
                    echo "Multiline shell steps works too"
                    ls -lah
                '''
                retry(3) {
                    sh 'echo "retry"'
                }
            }
        }
    }
}