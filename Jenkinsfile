pipeline {
    agent any

    stages {
        stage ('SCM') {
            steps {
                git branch: 'main', url: 'https://github.com/C1-80468/Sunproject.git'
            }
        }
        stage ('docker login') {
            steps {
                sh 'echo dckr_pat_8h7X3XtBZFmsjPP7CjmEDCT5RHE | /usr/bin/docker login -u c180468 --password-stdin'
            }
        }
        stage ('docker build image') {
            steps {
                sh '/usr/bin/docker image build -t c180468/mywebsite .'
            }
        }
        stage ('docker push image') {
            steps {
                sh '/usr/bin/docker image push c180468/mywebsite'
            }
        }
        stage ('docker remove service') {
            steps {
                sh '/usr/bin/docker service rm myservice'
            }
        }
        stage ('docker create service') {
            steps {
                sh '/usr/bin/docker service create --name myservice -p 9090:80 --replicas 5 c180468/mywebsite'
            }
        }
    }
}

