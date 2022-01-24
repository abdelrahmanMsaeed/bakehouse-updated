pipeline {
  agent { label 'jenkins_ubuntu_slave_java11' }
  stages {
    stage('start') {
      steps {
        script {
        cleanWs()
        withCredentials([usernamePassword(credentialsId: 'dockerhub-credentials', usernameVariable: 'USERNAME', passwordVariable: 'PASSWORD')]) {
          sh """
              docker login -u "${USERNAME}" -p "${PASSWORD}"
              docker build -t abosaeed/jenkins_worker .
              docker push abosaeed/jenkins_worker
          """
        }
        
      }
      }
    }
  }
}
