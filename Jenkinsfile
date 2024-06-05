pipeline {
    agent any

    environment {
        DOCKER_HUB_CREDENTIALS = credentials('docker-hub-creds')
        GITHUB_REPO = 'https://github.com/ZoyaSumbul/SCD_Final_Exam.git'
    }

    stages {
        stage('Checkout Code') {
            steps {
                git branch: 'main', url: "${env.GITHUB_REPO}"
            }
        }

        stage('Build Frontend Image') {
            steps {
                script {
                    dir('client') {
                        sh 'docker build -t abz10141/20i0932_frontend .'
                    }
                }
            }
        }

        stage('Build Auth Image') {
            steps {
                script {
                    dir('Auth') {
                        sh 'docker build -t abz10141/20i0932_auth .'
                    }
                }
            }
        }

        stage('Build Classrooms Image') {
            steps {
                script {
                    dir('Classrooms') {
                        sh 'docker build -t abz10141/20i0932_classrooms .'
                    }
                }
            }
        }

        stage('Build Event-bus Image') {
            steps {
                script {
                    dir('event-bus') {
                        sh 'docker build -t abz10141/20i0932_event-bus .'
                    }
                }
            }
        }

        stage('Build Post Image') {
            steps {
                script {
                    dir('Post') {
                        sh 'docker build -t abz10141/20i0932_post .'
                    }
                }
            }
        }

        stage('Push Images to Docker Hub') {
            steps {
                script {
                    docker.withRegistry('https://registry.hub.docker.com', 'DOCKER_HUB_CREDENTIALS') {
                        sh 'docker push abz10141/20i0932_frontend'
                        sh 'docker push abz10141/20i0932_auth'
                        sh 'docker push abz10141/20i0932_classrooms'
                        sh 'docker push abz10141/20i0932_event-bus'
                        sh 'docker push abz10141/20i0932_post'
                    }
                }
            }
        }
    }

    post {
        success {
            echo 'Pipeline executed successfully'
        }
        failure {
            echo 'Pipeline failed'
        }
    }
}
