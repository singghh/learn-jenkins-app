pipeline {
    agent any

    stages {
        stage('Build') {
            agent{
                docker{
                    image 'node:latest'
                    reuseNode true
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
        stage('Test')
        {
            steps{
                sh 'test -f build/index.html'
            }
        }
    }
}