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
    stage('Build image docker'){
      steps {
        scripts {
          sh 'docker build -t myimage_nginx .'
          sh 'docker tag myimage_nginx vincentm:myimage_nginx'
        }
      }
    }
    stage('Deploiement application'){
      steps {
        scripts {
          sh 'docker rm image mynginx'
          sh 'docker rm -f $(docker ps -a)'
          sh 'docker run -d --name monapp --hostname monapp -p 8099:80 myimage_nginx'
        }
      }
    }
  }
}
