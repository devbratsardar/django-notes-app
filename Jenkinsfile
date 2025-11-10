@Library('shared') _ 
pipeline {
    agent any

    stages {
        stage('Code Pull') {
            steps {
                script{
                code_checkout('https://github.com/devbratsardar/django-notes-app.git','main')
                }
            }
        }
        stage('Code Build') {
            steps {
                script{
                docker_build("notesapp")
                }
            }
        }
        stage('Code Deploy') {
            steps {
                script{
                    deploy()
                }
            }
        }
    }
      
}
