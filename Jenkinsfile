pipeline {
    agent { label 'instance-sv-1' }
    
    stages {
        stage('Print Server IP for Confirmation') {
            steps {  
                sh 'hostname -I'
            }
        }

        stage('Run the Ansible Playbook') {
            steps {
                sh '''
                    ansible-playbook -i inventory.ini playbook.yml
                '''
            }
        }
	
	stage('Give Permissions to tomcat war file'){
	   steps{ 
		sh '''
		sudo chown -R sree-vidya:sree-vidya /home/sree-vidya/tomcat-war 
                sudo chmod 700 /home/sree-vidya/tomcat-war 
                id
		'''
	}
	}
        stage('Maven Clean Install') {
            steps {
                dir('/home/sree-vidya/tomcat-war/') {
                    sh 'mvn clean install'
                }
            }
        }

        stage('Copy WAR and Restart Tomcat') {
            steps {
                sh '''
                    sudo systemctl stop tomcat
                    cp /home/sree-vidya/tomcat-war/target/ROOT.war /opt/tomcat-war/webapps/ROOT.war
                    sudo systemctl start tomcat
                '''
            }
        }
    }
}

