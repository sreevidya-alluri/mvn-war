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
          cd tomcat-root-war
           
           mvn clean install  
         
          '''
         }
      
    }
    
   
 }

}

