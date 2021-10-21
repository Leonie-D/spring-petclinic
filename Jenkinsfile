pipeline {
    agent any
    tools {
        maven 'MAVEN_HOME'
    }
    stages {
        stage('Build & Test') {
            steps {
                parallel(
                      test: {
                        sh 'mvn -B test --file pom.xml' 
                      },
                      build: {
                        sh 'mvn -B package -Dmaven.test.skip=true --file pom.xml' 
                      }
                    )
            }
        }
        stage ('Upload file') {
            steps {
                rtUpload (
                    // Obtain an Artifactory server instance, defined in Jenkins --> Manage Jenkins --> Configure System:
                    serverId: 'leonie',
                    spec: """{
                            "files": [
                                    {
                                        "pattern": "target/*.jar",
                                        "target": "default-maven-local/petclinic-${GIT_COMMIT.substring(0,8)}.jar"
                                    }
                                ]
                            }"""
                )
            }
        }
        stage('Cleanup Workspace') { 
            steps {
                cleanWs()
                sh """
                echo "Cleaned Up Workspace For Project"
                """
            }
        }
    }
}
