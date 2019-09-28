pipeline {
    agent any

    stages {
        stage('lint HTML') {
            steps {        
              sh 'echo "syntax checking"'     
              
            }
        } 
		stage('Build image') {
			steps{       
				docker.build("rajendran1166/pyweb")			
				}
		}		
    }
}