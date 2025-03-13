pipeline {
    agent any

    stages {
        stage('Build') {
            agent{
                docker{
                    image 'node:latest'
                }
            }
            steps{
                sh'''

                    ls -la
                    node -v
                    npm -v
                    npm ci
                    npm run build
                    echo "----List----"
                    ls -la

                '''
            }
        }
    }
}