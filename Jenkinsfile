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

        stage('mail') {
          steps {
            mail(subject: 'build', body: 'log', from: , to: 'jerome.nox@gmail.com')
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
