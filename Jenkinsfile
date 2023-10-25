pipeline {
  agent {label 'imageserver'}

  stages {
    stage('Add Proxy for Internet Connection') {
      steps {
        sh '''
          export http_proxy=http://172.17.89.251:8080
          export https_proxy=http://172.17.89.251:8080
        '''
      }      
    }
    stage('Install/Check packages') {
      steps {
        sh '''
          ansible --version
          ansible-playbook --version
          ansible-galaxy --version
        '''
      }      
    }
    stage('Run Ansible Build Image') {
      steps {
        sh 'ansible-galaxy collection install -r requirements.yml'
        sh 'ansible-playbook build_image.yml'
      }      
    }
  }
}
