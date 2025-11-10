@Library('shared') _ 
pipeline {
    agent any
     environment {
        DOCKERHUB_CREDS = credentials('dockerhub-credentials-id')
    }
    
    stages {
        stage('echo'){
            echo "pass : ${DOCKERHUB_CREDS_PSW}  # user: ${DOCKERHUB_CREDS_USR}"
        }
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
