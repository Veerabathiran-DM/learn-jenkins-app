pipeline {
    agent any

    stages {
        stage('Build') {
            agent {
                docker {
                    image 'node:22.14.0-alpine3.21'
                    reuseNode true
                }
            }
            steps {
                sh '''
                    ls -la
                    node --version
                    npm --version
                    npm install --package-lock-only
                    npm fund
                    chown -R 992:992 "/.npm"
                    npm audit fix
                    npm install react-scripts --save
                    npm run build
                    ls -la
                '''
                }
            }
        }
    }
