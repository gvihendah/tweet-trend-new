pipeline {
    agent {
        node {
            label "maven"
        }
    }
environment {
    PATH = "/opt/apache-maven-3.8.8/bin:$PATH"
}
    stages {
        stage("build") {
            steps {
                sh 'mvn clen deploy'
            }
        }
    }
}
