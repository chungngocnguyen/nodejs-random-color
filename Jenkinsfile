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
        stage('checkout'){
            steps{
                git branch: 'main', url: 'https://gitlab.com/deploya/task-manager.git'
            }
        }
            steps {
                script {
                    // Gọi hàm DockerBuild
                    DockerBuild(CONFIG_URI, DOCKERFILE, IMAGE_NAME, IMAGE_TAG)
                }
            }
        }
    }
