pipeline {
    agent any
	 def app 

    stages {
        stage('lint HTML') {
            steps {        
              sh 'echo "syntax checking"'     
              
            }
        } 
		stage('Build image') {
			steps{       
				app = docker.build("rajendran1166/pyweb")			
				}
		}		
    }
}