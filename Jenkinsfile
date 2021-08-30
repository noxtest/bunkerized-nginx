pipeline {
    agent any

    stages {
        stage('Build debian') {
            steps {
                sh 'sudo docker build -t debian-systemd -f tests/Dockerfile-debian .'
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
    }
}
