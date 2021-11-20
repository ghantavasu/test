node{
    def mvnHome
 
   stage('SetEnv') { 
      git 'https://github.com/cltalam/Snykscriptbasedintegration.git'
      mvnHome = tool 'MAVEN_HOME'
	   
   }
   
   stage('CompileandPackage') {
      withEnv(["MVN_HOME=$mvnHome"]) {
            bat(/"%MVN_HOME%\bin\mvn" -Dmaven.test.failure.ignore clean compile/)
         }
      
   }
   stage('Snyk'){
        snykSecurity failOnIssues: false, organisation: '0a9abaf4-c5e7-4e79-bd0d-94090771174a', snykInstallation: 'Snyk', snykTokenId: 'snykkey'
       
   }

}
