pipeline {
    agent my_main

    stages {
        stage('liquibase Status') {
            steps {
                sh '''liquibase status --verbose'''
            }
        }
        stage('liquibase updateSQL') {
            steps {
                sh '''liquibase updateSQL'''
            }
        }
       stage('Peform Update with Approval') {
            input{
                message "Do you want to proceed with update?"
            }
            steps {
                sh '''liquibase update'''
            }
        }
        stage('liquibase rollbackCount') {
            input{
                message "Would you like to rollback last commit?"
            }            
            steps {
                sh '''liquibase rollbackCount 1'''
            }
        }        
    }
}
