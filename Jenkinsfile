pipeline {
  agent {label 'imageserver'}

  stages {
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
