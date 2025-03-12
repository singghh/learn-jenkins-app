pipeline{
    agent any
    stages{
        agent{
            docker{
                image 'node:latest'
                reuseNode true
            }
        }
        stage("Build")
        {
            sh '''
            
                ls -la
                node -v
                npm -v
                npm ci
                npm run build
                echo 'List Data'
                ls -la
            '''
        }
    }
}
