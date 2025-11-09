pipeline {
    agent any

    stages {
        stage('Code Pull') {
            steps {
                git branch: 'main', url: 'https://github.com/devbratsardar/django-notes-app.git'
                echo 'code pull successfully'
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
