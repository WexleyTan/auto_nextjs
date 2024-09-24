pipeline {
    agent {
        label 'b'
    }
    stages {
        stage('Test') { 
            steps {
                sh ' docker ps ' 
            }
        }
    }
}
