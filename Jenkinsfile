pipeline {
    agent {
        node {
            label "maven"
        }
    }

    stages {
        stage('git-clone') {
            steps {
                git branch: 'main', url: 'https://github.com/gvihendah/tweet-trend-new.git'
            }
        }
    }
}
