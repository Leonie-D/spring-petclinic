pipeline {
    agent any
    tools {
        maven 'Maven 3.3.9'
        jdk 'jdk8'
    }
    stages {
        stage('build') {
            steps {
                sh 'mvn -B package -Dmaven.test.skip=true --file pom.xml' 
            }
        }
    }
}
