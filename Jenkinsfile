@Library('shared') _ 
pipeline {
    agent any
     environment {
        DOCKERHUB_CREDS = credentials('dockerhub-credentials-id')
    }
    
    stages {
        stage('echo'){
            steps {
               echo  "pass: ${DOCKERHUB_CREDS_PSW}  # user: ${DOCKERHUB_CREDS_USR}"
            }
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
                docker_build("${DOCKERHUB_CREDS_USR}","notesapp")
                }
            }
        }
        stage('Code Push') {
            steps {
                script{
                docker_push("${DOCKERHUB_CREDS_USR}", "${DOCKERHUB_CREDS_PSW}","${DOCKERHUB_CREDS_USR}/notesapp")
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
