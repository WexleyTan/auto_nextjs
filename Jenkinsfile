pipeline {
  agent any
  tools {
    nodejs 'nodejs'
  }
  stages {
    stage("build") {
      steps {
        echo "🚀 Building the application"
        sh 'docker build -t nextjs_jenkins .'
      }
    }
    }
  }


