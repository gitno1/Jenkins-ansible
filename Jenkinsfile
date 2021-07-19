pipeline {
    agent any
    stages {
        stage('Setup parameters') {
            steps {
                script { 
                    properties([
                        parameters([
                            string(
                                defaultValue: '', 
                                name: 'VM IP', 
                                trim: true
                            ),
                            string(
                                defaultValue: '', 
                                name: 'VM Admin User', 
                                trim: true
                            ),
                            string(
                                defaultValue: '', 
                                name: 'VM Password', 
                                trim: true
                            )
                        ])
                    ])
                }
            }
        }
        stage('Ansible Playbook') {
            steps {
                ansiblePlaybook credentialsId:'private-key',disableHostKeyChecking:true,installation:'ansible2',inventory:'dev.inv',playbook:'windows_update.yml'
            }
        }
    }   
}
