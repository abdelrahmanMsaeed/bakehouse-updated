pipeline {
  agent any
  stages {
    stage('deploy using k8s') {
      steps {
        script {
        withCredentials([file(credentialsId: 'kubecongif', variable: 'k8s_config')]) {
          sh """
              kubectl delete -f . --kubeconfig=$k8s_config
              kubectl apply -f . --kubeconfig=$k8s_config

          """
        }
        
      }
      }
    }
  }
}
