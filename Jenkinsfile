pipeline {
    agent any

    stages {
        stage('Verify Branch') {
            steps {
                echo "$GIT_BRANCH"
                sh(script: 'echo Hello world')
            }
        }
    }
}