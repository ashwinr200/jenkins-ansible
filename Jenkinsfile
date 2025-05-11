pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                git branch: 'main', url: 'https://github.com/ashwinr200/jenkins-ansible.git'
            }
        }

        stage('Run Ansible Playbook') {
            steps {
                ansiblePlaybook(
                    credentialsId: 'ansible-ssh',
                    disableHostKeyChecking: true,
                    installation: 'ansible2',
                    inventory: '/etc/ansible/hosts',
                    playbook: 'install_ngnix.yml'
                )
            }
        }
    }

    post {
        success {
            echo 'Ansible playbook executed successfully.'
        }
        failure {
            echo 'Ansible playbook failed.'
        }
    }
}

