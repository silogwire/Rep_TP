node {

        stage('Clone') {
                git 'https://github.com/silogwire/Rep_TP.git'
        }
        stage('Build') {
                sh label: '', script: 'mvn clean compile'
        }
	 stage('Unit Tests') {
   
   	 sh label: '', script: 'mvn test'
  	 }
 }

