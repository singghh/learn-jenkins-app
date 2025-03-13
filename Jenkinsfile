pipeline{
    agent any
    options{
        reuseNode true
    }
    stages{
        stage('Build'){
            agent{
                docker{
                    image 'node:latest'
                }
            }
            steps{
                sh '''
                    ls -la
                    node -v
                    npm -v
                    npm run build
                    echo "List Data"
                    ls -la
                '''
            }
        }
    }
}