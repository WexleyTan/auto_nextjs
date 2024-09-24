pipeline {
      agent { label "b" }
    tools {
        nodejs 'nodejs'
    }
    environment {
        IMAGE = "neathtan/nextjs_cd"
        DOCKER_IMAGE = "${IMAGE}:${BUILD_NUMBER}"
        DOCKER_CREDENTIALS_ID = 'neathtan'
        GIT_MANIFEST_REPO = "https://github.com/WexleyTan/nextjs_manifest.git"
        GIT_BRANCH = "main"
        MANIFEST_REPO = "manifest-repo"
        MANIFEST_FILE_PATH = "deployment.yaml"
        GIT_CREDENTIALS_ID = 'wexley_Pass'
    }
      
        stage("build and push docker image") {

            steps {
                script {
                    echo "🚀 Building docker image..."
                    sh ' docker build -t ${DOCKER_IMAGE} .'
                    sh ' docker images | grep -i ${IMAGE} '
                    }
                    echo "🚀 Pushing the image to Docker hub"
                    sh 'docker push ${DOCKER_IMAGE}'   
                }
            }
        }
