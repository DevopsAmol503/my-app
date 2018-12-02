node('mavel-lable'){
   def mvnHome
   stage('Preparation') { // for display purposes
      // Get some code from a GitHub repository
      git branch: '$(branch)', url: 'https://github.com/DevopsAmol503/my-app.git'
      mvnHome = tool name: 'maven3.6.0', type: 'maven'
   }
   stage('Build') {
      // Run the maven build
      if (isUnix()) {
         sh "'${mvnHome}/bin/mvn' -Dmaven.test.failure.ignore clean package"
      } else {
         bat(/"${mvnHome}\bin\mvn" -Dmaven.test.failure.ignore clean package/)
      }
   }
   stage('Results') {
      junit '**/target/surefire-reports/TEST-*.xml'
         // archiveArtifacts 'my-app-1.0-SNAPSHOT.jar'
    // archiveArtifacts '**/target/my-app-1.0-SNAPSHOT.jar'

      
   }
}
