pipeline {
    agent any

    stages {
        stage('Build') {
            agent {
                docker {
                    image 'node:18-alpine'
                    args '-u root'
                    reuseNode true
                }
            }
            steps {
                sh '''
                    ls -la
                    node --version
                    npm --version
                    rm -rf node_modules package-lock.json
                    npm cache clean --force
                    npm ci
                    npm run build
                '''
            }
        }
        stage('Test'){
            steps{
            echo "Test stage"
            }
        }
    }
}
