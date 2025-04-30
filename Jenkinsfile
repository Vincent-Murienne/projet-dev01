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
        git credentialsId: 'id-user-github', url: 'https://github.com/Vincent-Murienne/projet-dev01.git'
      }
    }
    stage('Build image docker'){
      steps {
        script {
          sh 'docker build -t myimage_nginx .'
          sh 'docker tag myimage_nginx vincentm:myimage_nginx'
          sh 'docker images'
        }
      }
    }
    stage('Deploiement application'){
      steps {
        script {
          sh 'docker rm -f $(docker ps -aq) || true'
          sh 'docker run -d --name monapp --hostname monapp -p 8099:80 myimage_nginx'
          sh 'docker exec monapp "ifconfig"'
        }
      }
    }
  }
}
