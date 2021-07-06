pipeline {
  agent any
    stages {
        stage('Setup parameters') {
            steps {
                script {
                    properties([
                        parameters([
                            string(
                                defaultValue: 'Administrator',
                                name: 'ansibleuser',
                                trim: true
                            ),
                            string(
                                defaultValue: 'Testpwd123**!',
                                name: 'password',
                                trim: true
                            ),
                            string(
                                defaultValue: '10.0.0.1',
                                name: 'ip',
                                trim: true
                            )
                        ])
                    ])
                }
            }
        }
        stage('Create Inventory') {
            steps {
                sh """
                #!/bin/bash
                cat >inv <<EOF
                [winserver]
                ${ip}
                """
            }
        }
        stage ('Windows Update') {
            steps {
                  sh '''
                  ansible-playbook -i inv /var/lib/jenkins/playbook.yaml --extra-vars "ansible_user=${ansibleuser} ansible_password=${password} ansible_port=5986 ansible_connection=winrm ansible_winrm_server_cert_validation=ignore"
                  '''
            }
        }

    }
 }
