pipeline{
  agent any 
  stages{
    steps{
      dir("/home/sree-vidya/tomcat-war"){
        sh "mvn clean install"
     }   
    } 
  } 
  stages{
    steps{ 
    sh "cp ./target/ROOT.war /opt/tomcat/webapps/ROOT.war"
   }
 } 
  
}
