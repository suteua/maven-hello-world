node {
 stage('Checkout') 
 {   
    checkout scm; 
 }
 stage('MVN clean and validate') 
 {
  sh '''mvn clean validate '''     
 }

  stage('Create package')
 {
  sh '''mvn package '''
 }
   
}
