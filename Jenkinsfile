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
            agent{
                docker{
                    image 'node:latest'
                    reuseNode true
                }
            }
            steps{
                sh '''
                    test -f build/index.html
                    npm test
                '''
            }
        }
        stage('Deploy') {
            agent{
                docker{
                    image 'node:latest'
                    reuseNode true
                }
            }
            steps{
                sh'''
                    npm install netlify-cli -g
                    netlify --version 
                '''
            }
        }
    }
    post{
        always{
            junit 'test-results/junit.xml'
        }
    }
}