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
    }
}
pipeline {
    agent any

    stages {
        stage('Build debian') {
            steps {
                sh 'sudo docker build -t ubuntu-systemd -f tests/Dockerfile-ubuntu .'
            }
        }
        stage('Test') {
            steps {
                sh 'sudo ./tests/linux-run.sh ubuntu-systemd test-ubuntu'
            }
        }
        stage('Deploy') {
            steps {
                echo 'Deploying....'
            }
        }
    }
}
