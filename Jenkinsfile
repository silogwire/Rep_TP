pipeline {
 agent any
   environment {
 		 SONARQUBE_URL = "http://79.137.37.35"
 		 SONARQUBE_PORT = "9000"
 		 SONARQUBE_LOGIN = "7feb11a80127b3e132ef98b518d67e4115959d1a"
	 }
    stages {
        stage('Clone') {
		steps {
              		  git 'https://github.com/silogwire/Rep_TP.git'
       		 }
	}
        stage('Build') {
                steps {

               		 sh 'mvn clean compile'
       		 }
	}
	 stage('Unit Tests') {
                steps {
   			 sh 'mvn test'
		}
		post {
		    always {
    			 junit 'target/surefire-reports/**/*.xml'
   		    }
		}
  	 }

         stage('Integration Tests') {
                steps {
//	        	 sh label: '', script: 'mvn verify -Dsurefire.skip=true'
//        	 }
//		 post {
//			 always {
//    				 junit 'target/failsafe-reports/**/*.xml'
//   			 }
//   			 success {
   				  stash(name: 'artifact', includes: 'target/*.jar')
    				  stash(name: 'pom', includes: 'pom.xml')
   				  // to add artifacts in jenkins pipeline tab (UI)
   				  archiveArtifacts 'target/*.jar'
//   			 }              
		 }
	}

//	stage('Code Quality Analysis') {
//		steps {
//			sh 'mvn sonar:sonar -Dsonar.projectKey=sonarqube_Hello \
//                                            -Dsonar.host.url=$SONARQUBE_URL:$SONARQUBE_PORT \
//                                            -Dsonar.login=$SONARQUBE_LOGIN'
//		}
//	}

	stage('Sonarqube') {
	    steps {
	        withSonarQubeEnv('sonarqube') {
                      sh 'mvn clean package sonar:sonar -Dsonar.login=$SONARQUBE_LOGIN'

        }
    }
  }

}
}
