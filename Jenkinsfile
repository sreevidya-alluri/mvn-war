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

        stage('Maven Clean Install') {
            steps {
                dir('/home/sree-vidya/tomcat-root-war/') {
                    sh 'mvn clean install'
                }
            }
        }

        stage('Copy WAR and Restart Tomcat') {
            steps {
                sh '''
                    sudo systemctl stop tomcat
                    cp /home/sree-vidya/tomcat-root-war/target/ROOT.war /opt/tomcat/webapps/ROOT.war
                    sudo systemctl start tomcat
                '''
            }
        }
    }
}

