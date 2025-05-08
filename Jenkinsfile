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
           mvn clean install 
          '''
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

