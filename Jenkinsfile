pipeline {
    agent any
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
