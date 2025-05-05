pipeline {
    agent {label 'instance-sv-1'}
    stages {
	stage('print the server ip for confirmation'){
	 steps{  
            sh 'hostname -I'
          }
        } 
	stage('Run the playbook'){
        steps{
          sh "
	  ansible-playbook -i inventory.ini playbook.yml
	"
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
                sh " 
                     sudo systemctl stop tomcat
                     cp /home/sree-vidya/tomcat-root-war/target/ROOT.war /opt/tomcat/webapps/ROOT.war
                     sudo systemctl start tomcat
                   "
            }
        }
    }
}

