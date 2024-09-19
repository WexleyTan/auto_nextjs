pipeline {
    agent any
    tools {
        nodejs 'nodejs'
    }

    stages {
        stage("testVersion") {
            steps {
                echo "🚀 Checking node version "
                sh ' node --version '
            }
        }
    }

    stages {
        stage("build") {
            steps {
                echo "🚀 Building the application"
                sh 'docker build -t nextjs_demo .'
            }
        }

        stage("deploy") {
            steps {
                echo '🚀 Deploying the application'
                sh 'docker stop nextjs_jenkins'
                sh 'docker run --name nextjs_jenkins -d -p 3001:3000 nextjs_demo'
                sh 'docker ps'
                echo "🚀🚀🚀"
            }
        }
    }
}
