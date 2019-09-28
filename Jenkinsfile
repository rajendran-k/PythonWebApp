pipeline {
    agent any

    stages {
        stage('lint HTML') {
            steps {        
              sh 'echo "syntax checking"'     
              sh 'tidy -q -e *.html'
            }
        }         
        }
     }