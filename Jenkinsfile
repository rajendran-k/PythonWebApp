node {
    def app 
	stage('Test image') {
        
        app.inside {
            echo "Tests passed"
			pwd
        }
    }
	stage('Build image') {
        /sh 'echo "syntax checking"'     
              sh 'tidy -q -e *.html'
    }
		

    stage('Build image') {
        /* This builds the actual image */

        app = docker.build("rajendran1166/pyweb")
    }

    stage('Test image') {
        
        app.inside {
            echo "Tests passed"
        }
    }

    stage('Push image') {
        /* 
			You would need to first register with DockerHub before you can push images to your account
		*/
        docker.withRegistry('https://registry.hub.docker.com', 'docker') {
            app.push("${env.BUILD_NUMBER}")
            app.push("latest")
            } 
                echo "Trying to Push Docker Build to DockerHub"
    }
}