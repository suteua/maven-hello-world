node {
 stage('Checkout') 
 {   
    checkout scm; 
 }
 stage('list env varibles')
 {
  echo "${env.BRANCH_NAME}"
  echo "${env.GIT_COMMIT}"
}

 stage('curentBuild')
 {
  echo "${currentBuild.startTimeInMillis}" 
  echo "Curent build number is: ${currentBuild.number}"
    echo "Curent build result is: ${currentBuild.result}"
  echo "change set is : ${currentBuild.changeSets}" 
}

 stage('build')
 {
  sh 'printenv'
  
 }

 stage('Parsing project pom.xml')
 {
 
  def pom = readMavenPom file: 'pom.xml'
   echo "${pom.packaging}"
   echo "${pom.version}"
   echo "${pom.artifactId}"
 }  
}
