pipeline {
	agent any
	stages {
	  stage('Github Pull') {
	    steps {
	      git branch: 'main',url:'https://github.com/minsssssd/cicd-test.git'
	    }
	  }
	  stage('Git clone end') {
           steps {
	     sh 'touch cicd_test.txt'
	     sh 'echo "git clone end" > cicd_test.txt'
           }
      }
	  stage('Deploy Server') {
		steps{
			sshagent(credentials:['Deploy-Privatekey']){
			sh "sudo scp -o StrictHostKeyChecking=no index.html ubuntu@13.124.90.34:/var/www/html/"
			}
		}
	  }
    }
}
