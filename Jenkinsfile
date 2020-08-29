pipeline {
  agent any
  stages {
    stage('SCM Checkout') {
      steps {
        echo '>>> Start getting SCM code'
        git 'https://github.com/khalednoh/demo2.git'
        echo '>>> End getting SCM code'
      }
    }

    stage('Build') {
      steps {
        echo 'testing completed >>>>>>'
      }
    }

    stage('Deploy') {
      steps {
        echo 'deployed successfully >>>>'
      }
    }
    stage('Notification') {
      steps {
        echo 'Dears, a new build has been completed successfully >>>><<<<'
      }
    }

  }
}
