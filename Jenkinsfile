node('any'){
     tools { 
          maven 'MAVEN_HOME' 
          jdk 'JAVA_HOME' 
           }
   
   def MAVEN_HOME='C:\Users\Amol Bhoj\Desktop\Devops\apache-maven-3.9.0\'
   stage('SCM Checkout- Preparation') { // for display purposes
      // Get some code from a GitHub repository
     // withCredentials([usernamePassword(credentialsId: 'jenkins-git-key', passwordVariable: 'pass', usernameVariable: 'user')]) {
    // the code here can access $pass and $user
}
      git branch: 'master', url: 'https://github.com/DevopsAmol503/my-app.git'
      credentialsId: 'jenkins-git-key'
     // git clone https://github.com/DevopsAmol503/my-app.git
      mvnHome = tool name: 'maven3.9.0', type: 'maven'
   }
   stage('Build') {
      // Run the maven build
      if (isUnix()) {
         sh "'${mvnHome}/bin/mvn' -Dmaven.test.failure.ignore clean package"
      } else {
         bat(/"${env.MAVEN_HOME}\bin\mvn" -Dmaven.test.failure.ignore compile/)
         bat(/"${env.MAVEN_HOME}\bin\mvn" -Dmaven.test.failure.ignore clean package/)
      }
   }
   stage('Results') {
      junit '**/target/surefire-reports/TEST-*.xml'
         // archiveArtifacts 'my-app-1.0-SNAPSHOT.jar'
    // archiveArtifacts '**/target/my-app-1.0-SNAPSHOT.jar'

      
   }
}
