pipeline {
  agent any
  tools { 
        maven 'maven 3_2_5'  
    }
   stages{
    stage('CompileandRunSonarAnalysis') {
            steps {	
		sh 'mvn clean verify sonar:sonar -Dsonar.projectKey=tamie -Dsonar.organization=tamie -Dsonar.host.url=https://sonarcloud.io -Dsonar.token=99176cf1baf9dc68b833361f0dd72c4cbb07c2a7'
			}
        } 
	   stage('Run Snyk Static Code Analysis') {
            steps {
		    withCredentials([string(credentialsId: 'SNYK_TOKEN', variable: 'SNYK_TOKEN')]) {
			    sh 'mvn snyk:test -fn'
		    }
	    }
   }
 }
}
