@Library("Shared") _
pipeline {
    agent {
        label 'demo'
    }
    stages {
        stage("Hello"){
            steps{
                script{
                    hello()
                }
            }
        }
        stage("Clone") {
            steps {
                echo "Clonig the repo from GitHub"
                script{
                    clone("https://github.com/AmitTheCloud/django-notes-app.git","dev")
                }
            }
        }
        stage("Build") {
            steps {
                echo "Building the Image"
                script{
                    build("asolanki1811","notes-app","latest")
                }
            }
        }
        stage("Push to DockerHub") {
            steps {
                echo "This is pushing the images to Docker Hub"
                script{
                    push("notes-app","latest","asolanki1811")
                }
            }
        }
        stage("Deploy") {
            steps {
                echo "Deploying the Application"
                sh "docker compose up -d"
            }
        }
    }
}
