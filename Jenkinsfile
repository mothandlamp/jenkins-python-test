pipeline {
    agent {
        docker {
            image "python:latest"
            args "-u root"
        }
    }

    stages {
        stage("install deps") {
            steps {
                sh "pip3 install -r requirements.txt"
            }
        }
        stage("tests") {
            steps {
                sh "coverage run -m nose2 -v"
            }
         }
        stage("reports") {
            steps {
                sh "coverage html"
		sh "coverage xml"
                sh "coverage report"
            }
        }
    }
    post {
        always {
            archiveArtifacts artifacts: "htmlcov/**", fingerprint: true
            cobertura coberturaReportFile: "coverage.xml"
        }
    }
}
