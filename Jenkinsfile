pipeline {
    agent any
    tools {
        maven 'MAVEN_HOME'
    }
    stages {
        stage('build') {
            steps {
                sh 'mvn -B package -Dmaven.test.skip=true --file pom.xml' 
            }
        }
    }
}
