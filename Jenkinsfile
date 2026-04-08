pipeline {
	agent any

	environment {
		strDockerImage="mindollss/cicd-test:0.1"
	}
	stages {
	  stage('Github Pull') {
	    steps {
	      git branch: 'main',url:'https://github.com/minsssssd/cicd-test.git'
	    }
	  }
	  stage('Docker Image Build') {
           steps {
			script {
				oDockImage = docker.build(strDockerImage,"-f Dockerfile .")
			}
		   }
      }
	  stage('Deploy Server') {
		steps{
			sshagent(credentials:['Deploy-Privatekey']){
			sh "scp -o StrictHostKeyChecking=no index.html ubuntu@13.124.90.34:/home/ubuntu/"
			sh "ssh -o StrictHostKeyChecking=no ubuntu@13.124.90.34 sudo cp /home/ubuntu/index.html /var/www/html/"
			}
		}
	  }
    }
}
