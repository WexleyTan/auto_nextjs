pipeline {
      agent { label "b" }
    tools {
        nodejs 'nodejs'
    }
    environment {
        IMAGE = "neathtan/nextjs_cd"
        DOCKER_IMAGE = "${IMAGE}:${BUILD_NUMBER}"
        DOCKER_CREDENTIALS_ID = 'docker_hub'
        GIT_MANIFEST_REPO = "https://github.com/WexleyTan/nextjs_manifest.git"
        GIT_BRANCH = "main"
        MANIFEST_REPO = "manifest-repo"
        MANIFEST_FILE_PATH = "deployment.yaml"
        GIT_CREDENTIALS_ID = 'wexley_Pass'
        
    }

    stages {
      stage("checkout") {
        steps {
          echo "🚀🤖 Running..."
          echo "Running on $NODE_NAME"
          echo "${BUILD_NUMBER}"
          sh ' docker image prune --all '
          sh ' pwd '
          sh 'ls'
        }
      }

        stage("build and push docker image") {

            steps {
                script {
                    echo "🚀 Building docker image..."
                    sh ' docker build -t ${DOCKER_IMAGE} .'
                    sh ' docker images | grep -i ${IMAGE} '
                    
                    echo "🚀 Log in Docker hub using Jenkins credentials..."
                    withCredentials([usernamePassword(credentialsId: DOCKER_CREDENTIALS_ID, passwordVariable: 'DOCKER_PASS', usernameVariable: 'DOCKER_USER')]) {
                      sh 'echo "${DOCKER_PASS} ${DOCKER_USER}" '
                      sh 'echo $DOCKER_PASS | docker login -u $DOCKER_USER --password-stdin'
                    }
                    echo "🚀 Pushing the image to Docker hub"
                    sh 'docker push ${DOCKER_IMAGE}'
                    
                }
            }
        }
  }
}
