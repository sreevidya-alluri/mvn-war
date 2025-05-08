pipeline {
    agent any
    
    stages {
        stage('Print Server IP for Confirmation') {
            steps {  
                sh 'hostname -I'
            }
        }
      
       
     stage('Do mvn clean install'){
      steps{
       dir('/home/sree-vidya/tomcat-war'){  
         sh '''
           mvn clean install 
          '''
         }
      }
    }
    
    stage('Run the playbook'){
     steps{   
     sh ''' ansible-playbook -i inventory.ini playbook.yml
'''
}
}
 }

}

