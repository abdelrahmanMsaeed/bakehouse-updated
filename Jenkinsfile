pipeline {
  agent { label 'jenkins_ubuntu_slave_java11' }
  stages {
    stage('deploy using k8s') {
      steps {
        script {
        withCredentials([file(credentialsId: 'kubecongif', variable: 'k8s_config')]) {
          sh """
              gcloud container clusters get-credentials my-gke-cluster --region us-central1 --project abdelrahman-saeed
              kubectl delete -f . --kubeconfig=$k8s_config
              kubectl apply -f . --kubeconfig=$k8s_config

          """
        }
        
      }
      }
    }
  }
}
