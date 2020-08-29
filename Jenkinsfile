pipeline {
  agent any
  stages {
    stage('SCM Checkout') {
      steps {
        echo '>>> Start getting SCM code'
        git 'https://github.com/khalednoh/demo1.git'
        echo '>>> End getting SCM code'
      }
    }

    stage('Build JAR') {
      steps {
        echo '>>> Start building using Maven'
        sh 'mvn -Dmaven.test.skip=TRUE install'
        echo '>>> End building using Maven'
      }
    }

    stage('Build Docker Image') {
      steps {
        echo '>>> Start building App docker image'
        sh "docker build -t $MyDockerAccountName/$MyDockerReposioryName:$MyTagName$BUILD_NUMBER --pull=true $WORKSPACE"
        echo '>>> End building App docker image'
      }
    }

    stage('Upload Docker Image') {
      steps {
        echo '>>> Start uploading the docker image'
        withCredentials([string(credentialsId: 'DockHubSecret', variable: 'DockerHubIDSecret')]) {
            sh "docker login -u $MyDockerAccountName -p $DockerHubIDSecret"
        }
        sh "docker push $MyDockerAccountName/$MyDockerReposioryName:$MyTagName$BUILD_NUMBER"
        echo '>>> End uploading the docker image'
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
  environment {
    MyDockerAccountName = 'khalednoh'
    MyDockerReposioryName = 'pipeline-demo'
    MyTagName = 'Jenkins-pipeline-Demo'
  }
}
