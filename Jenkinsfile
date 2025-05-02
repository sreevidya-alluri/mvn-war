pipeline {
    agent {label 'instance-sv-1'}
    stages {
	stage('print the server ip for confirmation'){
	 steps{  
            sh 'hostname -I'
          }
        }
        stage('maven clean install') {
            steps {
                dir("/home/sree-vidya/tomcat-root-war/") {
                    sh "mvn clean install"
                }
            }
        }
        stage('copy to the path') {
            steps {
                sh "cp /home/sree-vidya/tomcat-war/target/ROOT.war /opt/tomcat/webapps/ROOT.war"
            }
        }
    }
}

