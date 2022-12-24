pipeline {
    agent any
        tools{
        maven 'myn'
        }
    stages {
        stage('Build Application') {
            steps {
                sh "mvn -f pom.xml clean package"
            }
            post {
                success {
                    echo "Now Archiving the Artifacts...."
                    archiveArtifacts artifacts: "**/*.war"
                }
            }
        }

        stage('Create Tomcat Docker Image'){
            steps {
                sh "pwd"
                sh "docker build . -t tomcatsamplewebapp:${env.BUILD_ID}"
            }
        }

    }
}
//above script under tool 'myn' is a configured maven plugin name which is configured under the Global configure plugin option//
