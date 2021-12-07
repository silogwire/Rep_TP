pipeline {
 agent any
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
  	 }

         stage('Integration Tests') {
                steps {
	        	 sh label: '', script: 'mvn verify -Dsurefire.skip=true'
        	 }
	}
     }
}  

