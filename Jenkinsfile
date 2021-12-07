node {

        stage('Clone') {
                git 'https://github.com/silogwire/Rep_TP.git'
        }
        stage('Build') {
                sh label: '', script: 'mvn clean compile'
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

        	 sh label: '', script: 'mvn verify -Dsurefire.skip=true'
         }

 }

