node{
    def mvnHome
 
   stage('SetEnv') { 
      git 'https://github.com/ghantavasu/test.git'
      mvnHome = tool 'MAVEN_HOME'
	   
   }
   
   stage('CompileandPackage') {
      withEnv(["MVN_HOME=$mvnHome"]) {
            bat(/"%MVN_HOME%\bin\mvn" -Dmaven.test.failure.ignore clean compile/)
         }
      
   }
   stage('Snyk'){
        snykSecurity failOnIssues: false, organisation: 'a1c68847-d2a0-4a25-84ce-8b9de47cdd69', snykInstallation: 'Snyk', snykTokenId: 'snykkey'
       
   }

}
