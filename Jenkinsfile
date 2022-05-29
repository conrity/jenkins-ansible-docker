pipeline {
    agent {
      node {
          label 'master'
      }
    }

    stages {
        stage('Git checkout') {
            steps {
 	 checkout([$class: 'GitSCM', branches: [[name: '*/master']], doGenerateSubmoduleConfigurations: false, extensions: [], submoduleCfg: [], userRemoteConfigs: [[credentialsId: '', url: 'https://github.com/conrity/jenkins-ansible-docker.git']]]) 
            }
        }
        stage('Install wordpress on EC2 instance') {
            steps {
                sh """ 
                export ANSIBLE_HOST_KEY_CHECKING=False
                cd ansible-playbooks/
                pwd
                ls -l
                whoami
                ansible-playbook -i hosts deploy-wordpress.yml 
                """ 
                }            
        }
    }
}
