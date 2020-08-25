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
                sh(script: 'docker image prune --all -f')
            }
            post{
                success{
                    echo ":) prune successful"
                }
                failure{
                    echo ":( Prune failed"
                }
            }
        }
        stage('Docker Image Build'){
            steps{
                sh(script: 'docker ps -a')
                sh(script: 'docker images -a')
                sh(script: """
                    cd ubuntu
                    docker build -t jenkins-trivy .
                    docker images -a
                    cd ..
                """)
            }
        }
    }
}