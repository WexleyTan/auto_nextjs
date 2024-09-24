pipeline {
    agent {
        label 'b'
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
