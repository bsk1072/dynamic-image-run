pipeline {
   agent {
       label 'master' 
       
   }
  environment {
    registry = "docker_hub_account/bsk1072"
    registryCredential = 'bsk1072'
    customImage = ""
  }
    stages {
        stage('Checkout scm') {
          steps{
          checkout scm
              }
            }
          }
        stage('Setup Image Properties') {
          steps{
            script {
                customImage = docker.image(DOCKER_IMAGE)
              }
            }
          }
        stage('Deploy Image') {
          steps{
            script {
              docker.withRegistry( '', registryCredential ) {
            customImage.run('-p 8081:8080', '')
              }
            }
          }
        }
    }
}
