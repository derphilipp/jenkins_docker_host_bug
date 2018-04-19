pipeline {
  agent {
    dockerfile {
      label "docker"
        filename 'Dockerfile'
    }
  }
  stages{
    stage('Run something inside docker'){
      steps {
        echo 'I am running inside a docker container'
        sh 'hostname'
        sh 'figlet "Hello World"'
      }
    }
    stage('Run something outside docker on a different machine'){
      agent {
        label "raspberry"
        }
      options {
        skipDefaultCheckout()
      }
      steps{
        echo 'figlet does not exist here'
        echo 'also, this throws an exception'
        sh 'hostname'
      }
    }
  }
}
