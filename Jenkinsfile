pipeline {
 agent any
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
	        	 sh label: '', script: 'mvn verify -Dsurefire.skip=true'
        	 }
	}

}

