node {

 def mvnHome = tool 'M3'
 def mvnCmd="${mvnHome}/bin/mvn -s /var/jenkins_home/maven-global-settings-files.xml"
 
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
 
  sh "${mvnCmd} clean compile"
 }

 stage('build')
 {
  sh 'printenv'
  
 }

// stage('Parsing project pom.xml')
// {
 
//  def pom = readMavenPom file: 'pom.xml'
 //  echo "${pom.packaging}"
//   echo "${pom.version}"
//   echo "${pom.artifactId}"
//  }

  stage('SonarQube analysis') {
    withSonarQubeEnv('SonarQube') {
      // requires SonarQube Scanner for Maven 3.2+
     // sh 'mvn sonar:sonar'
       echo 'sonar'
    }
  }

 stage('Change set')
 {
 echo getChangeString()
 }

}

@NonCPS
def getChangeString() {
 MAX_MSG_LEN = 100
 def changeString = ""

 echo "Gathering SCM changes"
 def changeLogSets = currentBuild.changeSets
 for (int i = 0; i < changeLogSets.size(); i++) {
 def entries = changeLogSets[i].items
 for (int j = 0; j < entries.length; j++) {
 def entry = entries[j]
 truncated_msg = entry.msg.take(MAX_MSG_LEN)
 changeString += " - ${truncated_msg} [${entry.author}]\n"
 }
 }

 if (!changeString) {
 changeString = " - No new changes"
 }
 return changeString
 }
  
