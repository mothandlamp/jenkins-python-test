pipeline {
    agent {
        docker {
            image 'python:latest'
            args '-u root'
        }
    }

    stages {
        stage("install deps") {
            steps {
                sh "pip3 install -r requirements.txt"
            }
        }
        stage("test") {
            steps {
                sh "nose2 -v"
            }
         }
    }
}
