@Library('cicd-test@main') _
pipeline {
    agent any

    environment {
        SERVICE_NAME = "my-app"
        CONFIG_URI = "https://gitlab.com/devops-jenkin/test-jenkin.git"
        DOCKERFILE = "cicd/Dockerfile"
        IMAGE_NAME = "${env.BRANCH_NAME}/my-app"
        IMAGE_TAG = "${env.GIT_COMMIT.take(7)}"
    }

    stages {
        stage('Build Docker'){
            steps {
                script {
                    // Gọi hàm DockerBuild
                    DockerBuild(CONFIG_URI, DOCKERFILE, IMAGE_NAME, IMAGE_TAG)
                }
            }
        }
    }

    post {
        success {
            notifySuccess()
        }
    }
}
