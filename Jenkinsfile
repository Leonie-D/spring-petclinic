pipeline {
    agent { 
        node {
            label 'master'
        }
    }
    stages {
        stage('build') {
            steps {
                echo 'mvn --version'
            }
        }
    }
}
