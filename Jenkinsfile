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
    stage('Build Image through ansible on a VM') {
      steps {
        sh 'ansible-galaxy collection install -r requirements.yml'
        sh 'ansible-playbook build_image_cl.yml'
      }      
    }
    stage('Sync generated file from VM to pxeserver') {
      steps {
          // sh "rsync -av /home/devops/partclonedata/* rchengpxe:/srv/www/repos/blobs/rockyimage/"  
        echo "TODO- copy image from server to pxe"
      }
    }
  }
}
