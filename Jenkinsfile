pipeline {
    agent any	 

    stages {
        stage('lint HTML') {
            steps {        
              sh 'echo "syntax checking"'     
			  sh 'docker build --tag rajendran1166/pyweb '              
            }
        } 
		
    }
}