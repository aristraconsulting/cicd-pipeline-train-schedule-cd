pipeline {
    agent any
    stages {
        stage('Build') {
            steps {
                sh 'echo "Building..."'
                sh 'npm install'
                sh 'npm run build'
            }
        }
        stage('Test') {
            steps {
                sh 'echo "Testing..."'
                sh 'npm test'
            }
        }
        stage('Deploy to Dev') {
            steps {
                sh 'echo "Deploying to Dev..."'
                sh 'ssh dev-server "cd /var/www/app && git pull && npm install && pm2 restart app"'
            }
        }
        stage('Deploy to Prod') {
            steps {
                sh 'echo "Deploying to Prod..."'
                sh 'ssh prod-server "cd /var/www/app && git pull && npm install && pm2 restart app"'
            }
        }
    }
}
