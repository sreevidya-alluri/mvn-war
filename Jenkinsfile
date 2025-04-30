pipeline {
    agent any
    stages {
        stage('Build') {
            steps {
                dir("/home/sree-vidya/tomcat-war") {
                    sh "mvn clean install"
                }
            }
        }
        stage('Deploy') {
            steps {
                sh "cp /home/sree-vidya/tomcat-war/target/ROOT.war /opt/tomcat/webapps/ROOT.war"
            }
        }
    }
}

