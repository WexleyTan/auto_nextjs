pipeline {
    agent any

    tools {
        nodejs 'nodejs'
    }

    stages {
        stage('Build') {
            steps {
                sh 'npm install'
                sh 'npm run build'
            }
        }

        stage('Deploy') {
            steps {
                docker.image('neathtan/nextjs-web:latest').build()
                docker.image('neathtan/nextjs-web:latest').run('-v $HOME:/home/jenkins')
            }
        }
    }
}

