// pipeline {
//     agent {
//         node {
//             label "maven"
//         }
//     }
//     environment {
//         PATH = "/opt/apache-maven-3.8.8/bin:$PATH"
//         SONAR_TOKEN = credentials('sonarqube-token')
//     }
//     stages {
//         stage('Build') {
//             steps {
//                 sh 'mvn clean compile'
//             }
//         }
//         stage('Test') {
//             steps {
//                 sh 'mvn test'
//             }
//         }
//         stage('SonarQube analysis') {
//             environment {
//                 scannerHome = tool 'montana-sonar-scanner'
//             }
//             steps {
//                 withSonarQubeEnv('montana-sonarqube-server') {
//                     sh """
//                     ${scannerHome}/bin/sonar-scanner \
//                     -Dsonar.projectKey=montana-key_twittertrend \
//                     -Dsonar.organization=montana-key \
//                     -Dsonar.sources=src/main/java \
//                     -Dsonar.tests=src/test/java \
//                     -Dsonar.java.binaries=target/classes \
//                     -Dsonar.java.test.binaries=target/test-classes \
//                     -Dsonar.login=${SONAR_TOKEN} \
//                     -Dsonar.verbose=true \
//                     -Dsonar.sourceEncoding=UTF-8
//                     """
//                 }
//             }
//         }
//     }
// }



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
                sh 'mvn clean deploy'
            }
        }
    stage('SonarQube analysis') {
        environment {
            scannerHome = tool 'montana-sonar-scanner';

        }
        steps {
            withSonarQubeEnv('montana-sonarqube-server') { // If you have configured more than one global server connection, you can specify its name
      sh "${scannerHome}/bin/sonar-scanner"
        }
    }
  }
} 
}


