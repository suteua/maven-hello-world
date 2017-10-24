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

 stage('list env varibles')
 {
  echo "${env.BRANCH_NAME}"
  echo "${env.BUILD_URL}"
 }

 stage('curentBuild')
 {
  echo "${currentBuild.startTimeInMillis}" 
  echo "Curent build number is: ${currentBuild.number}"
    echo "Curent build result is: ${currentBuild.result}"
  echo "change set is : ${currentBuild.changeSets}" 
}
   
}
