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
       
         sh '''  
          cd tomcat-root-war
           
           mvn clean install  
         
          '''
         }
      
    }
    
   
 }

}

