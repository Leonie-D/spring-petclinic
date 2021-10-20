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
        stage ('Upload file') {
            steps {
                rtUpload (
                    // Obtain an Artifactory server instance, defined in Jenkins --> Manage Jenkins --> Configure System:
                    serverId: 'leonie',
                  //  spec: """{
                    //        "files": [
                      //              {
                      //                  "pattern": "target/*.jar",
                      //                  "target": "petclinic"
                      //              }
                      //          ]
                      //      }"""
                )
            }
        }
    }
}
