pipeline {
  agent any
  stages {
    stage('Supprimer le workspace'){
      steps {
        deleteDir()
      }
    }
    stage('Checkout SCM'){
      steps {
        sh 'git clone https://github.com/Vincent-Murienne/projet-dev01.git'
      }
    }
  }
}
