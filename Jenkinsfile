pipeline {
    agent any

    environment {
        DISABLE_AUTH = 'true'
        DB_ENGINE    = 'nodejs'
    }
    stages {
        stage('Test') { 
            steps {
                echo "Hello Camboida"
            }
        }
    stage('Docker Build') {
      steps {
        sh 'docker build -t neathtan/nextjs-web:tagname .'
      }
    }
}
}
