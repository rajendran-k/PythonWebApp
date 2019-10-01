node {
    def app

    stage('Clone repository') {
        /* Cloning the Repository to our Workspace */

        checkout scm
    }

    stage('Build image') {
        /* This builds the actual image */

        app = docker.build("rajendran1166/pyweb")
    }

    stage('Test image') {
        
        app.inside {
            sh 'pylint --disable=R,C,W1203,W0312 student.py'
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
	
	stage('Deploying') {
      echo 'Deploying to AWS...EKS'
      dir ('./') {
        withAWS(credentials: '34fbae67-03ae-4fc4-9e39-385f84000730', region: 'us-east-2') {
            sh "aws eks --region us-east-2 update-kubeconfig --name hell"
            sh "kubectl apply -f aws/aws-auth-cm.yaml"            
            sh "kubectl apply -f aws/deployment.yaml"
            sh "kubectl apply -f aws/next.yml"
            sh "kubectl get nodes"
            sh "kubectl get pods"            
        }
      }
    }
	stage("Cleaning up") {
      echo 'Cleaning up...'
      sh "docker system prune -f "
    }
	
}