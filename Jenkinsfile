pipeline {
    agent any

    stages {
        stage('Verify Branch') {
            steps {
                echo "$GIT_BRANCH"
                sh(script: 'echo Hello world')
            }
        }
        stage('Docker Build'){
            steps{
                sh(script: 'docker ps -a')
                sh(script: """
                    cd azure-vote
                    docker images -a
                    docker build -t jenkins-pipeline .
                    docker images -a
                    cd ..
                
                """)
            }

        }
    }
}