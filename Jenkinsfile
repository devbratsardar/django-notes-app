@Library('shared') _ 
pipeline {
    agent any

    stages {
        stage('Code Pull') {
            steps {
                script{
                code_checkout('https://github.com/devbratsardar/django-notes-app.git','main')
                }
                echo "done";
            }
        }
        stage('Code Build') {
            steps {
                sh "docker build -t notesapp ."
                echo 'Image build successfully'
            }
        }
        stage('Code Deploy') {
            steps {
                sh "docker run -d -p 8000:8000 notesapp:latest"
                echo 'deployed successfully'
            }
        }
    }
      
}
