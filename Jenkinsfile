pipeline {
  agent any
  stages {
    stage ('New Build Notifications') {
       parallel {
          stage ('Email notification') {
            steps {
                    echo '>>> Send New application build notification'
            }
         }
         stage ('Slack Notification') {
            steps {
              echo '>>> Send New Build Slack notifcation'            }
          }
        }
    }
    
    stage('SCM Checkout') {
      steps {
        echo '>>> Start getting SCM code'
      }
    }

    stage('Build JAR') {
      steps {
        echo '>>> Start building using Maven'
      }
    }

    stage('Build Docker Image') {
      steps {
        echo '>>> start clearing old docker images'
      }
    }

    stage('Upload Docker Image') {
      steps {
        echo '>>> Login to Docker hub'
      }
    }

    stage('Deploy') {
      steps {
        echo 'Start Killing and Removing old continaer'
      }
    }

  }
}
