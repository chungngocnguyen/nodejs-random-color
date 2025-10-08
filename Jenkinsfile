@Library('cicd-test@main') _
pipeline {
    agent any

    environment {
        CONFIG_URI = "https://gitlab.com/devops-jenkin/test-jenkin.git"
        DOCKERFILE = "cicd/Dockerfile"
        IMAGE_NAME = "${env.BRANCH_NAME}/my-app"
        IMAGE_TAG = "v1.0.0"
    }

    stages {
        stage('Build Docker'){
            steps {
                script {
                    // Gọi hàm DockerBuild
                    env.CI_COMMIT_SHORT = env.GIT_COMMIT.take(7)
                    echo "CI_COMMIT_SHORT = ${env.CI_COMMIT_SHORT}"
                    DockerBuild(CONFIG_URI, DOCKERFILE, IMAGE_NAME, IMAGE_TAG)
                }
            }
        }
    }
}
