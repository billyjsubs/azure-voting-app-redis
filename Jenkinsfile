pipeline {
    agent any

    stages {
        stage('Verify Branch') {
            steps {
                echo "$GIT_BRANCH"
                sh(script: 'echo Hello world')
            }
        }
        stage('Removed dangling images'){
            steps{
                sh(script: 'docker image prune -f')
            }
        }
        stage('Docker Build'){
            steps{
                sh(script: 'docker ps -a')
                sh(script: """
                    cd ubuntu
                    docker build -t jenkins-pipeline-ubuntu-python .
                    docker images -a
                    cd ..
                
                """)
            }

        }
    }
}