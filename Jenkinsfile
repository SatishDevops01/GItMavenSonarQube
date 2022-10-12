pipeline {
    agent any
	environment {
        scannerHome = tool 'sonar4'
    }
    tools {
        maven 'maven3'	
    }
    stages {
      stage('SCM Chekout'){
          steps {
             echo 'Code checkout from GIT'
             git credentialsId: 'GitSSHKey', url: 'https://github.com/SatishDevops01/GItMavenSonarQube', branch: 'master'
          }
      }
      stage('SonarQube analysis') {
		steps{	
			echo 'SonarQube Code Analysis'
            		echo "${scannerHome}/bin/sonar-scanner"
			
		     }
	}
      stage('Build Packages'){
          steps {
              echo 'Build the packages using Maven'
              echo "mvn clean install"
          }
	   post {
                success {
                    echo "Now Archiving the Artifacts....."
                    archiveArtifacts artifacts: '**/*.war'
                }
            }
      } 
   
   }
}
