pipeline {
  agent any
  stages {
    stage('Build debian') {
      parallel {
        stage('Build debian') {
          steps {
            sh 'sudo docker build -t debian-systemd -f tests/Dockerfile-debian .'
          }
        }

        stage('error') {
          steps {
            sh 'sudo docker rm -f 5160aaebf9fa5bbcbce3f18a0201f0794830856c9b998689b5395cea91dbd542'
          }
        }

      }
    }

    stage('Test') {
      steps {
        sh 'sudo ./tests/linux-run.sh debian-systemd test-debian'
      }
    }

    stage('Deploy') {
      steps {
        echo 'Deploying....'
      }
    }

    stage('Build ubuntu') {
      steps {
        sh 'sudo docker build -t ubuntu-systemd -f tests/Dockerfile-ubuntu .'
      }
    }

    stage('Test Ubuntu') {
      steps {
        sh 'sudo ./tests/linux-run.sh ubuntu-systemd test-ubuntu'
      }
    }

    stage('Build fedora') {
      steps {
        sh 'sudo docker build -t fedora-systemd -f tests/Dockerfile-fedora .'
      }
    }

    stage('Test fedora') {
      steps {
        sh 'sudo ./tests/linux-run.sh fedora-systemd test-fedora'
      }
    }

    stage('Build Centos') {
      steps {
        sh 'sudo docker build -t centos-systemd -f tests/Dockerfile-centos .'
      }
    }

    stage('Test Centos') {
      steps {
        sh 'sudo ./tests/linux-run.sh centos-systemd test-centos'
      }
    }

  }
}