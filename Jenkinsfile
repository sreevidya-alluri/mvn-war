    pipeline {
    agent any
    
    stages {
        stage('Print Server IP for Confirmation') {
            steps {  
                sh 'hostname -I'
            }
        }
                stage('clone repo'){
            steps {
                git url: 'https://github.com/AndriyKalashnykov/tomcat-root-war'
              }
    	}

            
                 
            
     stage('Do mvn clean install'){
      steps{
       
         sh '''  
           
           mvn clean install  
         
          '''
         }
      
    } 

    stage('run the playbook'){
      steps{
       
         sh '''  
           
           ansible-playbook -i /home/sree-vidya/mvn-war/inventory.ini /home/sree-vidya/mvn-war/playbook.yaml
         
          '''
         }
      
    }
    
   
 }

}

