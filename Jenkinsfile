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
