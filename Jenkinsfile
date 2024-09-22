pipeline {
    agent {
        docker {image 'neathtan/nextjs-web'}
    }
    stages {
        stage('Test') { 
            steps {
                sh 'node --version'
                sh 'env | sort'
            }
        }
    }
}
