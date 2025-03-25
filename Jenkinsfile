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
                withSonarQubeEnv('montana-sonarqube-server') {
                    sh """
                    ${scannerHome}/bin/sonar-scanner \
                    -Dsonar.projectKey=montana-key_twittertrend \
                    -Dsonar.organization=your-organization-name \
                    -Dsonar.sources=src \
                    -Dsonar.java.binaries=target/classes
                    """
                }
            }
        }
    }
}



// pipeline {
//     agent {
//         node {
//             label "maven"
//         }
//     }
// environment {
//     PATH = "/opt/apache-maven-3.8.8/bin:$PATH"
// }
//     stages {
//         stage("build") {
//             steps {
//                 sh 'mvn clean deploy'
//             }
//         }
//     stage('SonarQube analysis') {
//         environment {
//             scannerHome = tool 'montana-sonar-scanner';

//         }
//         steps {
//             withSonarQubeEnv('montana-sonarqube-server') { // If you have configured more than one global server connection, you can specify its name
//       sh "${scannerHome}/bin/sonar-scanner"
//         }
//     }
//   }
// } 
// }


