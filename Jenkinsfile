pipeline {
    agent {
        label 'b'
    }
    tool {
        nodejs 'nodejs'
    }
    stages {
        stage('Test') { 
            steps {
                sh ' docker ps ' 
            }
        }
    }
}
