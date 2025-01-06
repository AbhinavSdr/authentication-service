pipeline {	
	agent any	
	tools {	    
		maven 'my-maven'		
		jdk 'jdk-17'	
	}	
	stages {        
		stage('Clone'){			
			steps {git url:'https://github.com/AbhinavSdr/authentication-service.git', branch:'master'}
		}
		stage('Build'){			
			steps {bat "mvn clean install -DskipTests"}		
		}	
		// stage('Pre-Deploy'){
		// 	steps{bat "docker rm -f auth-cntr"
		// 				"docker rmi -f auth-img"}
		// }	
		stage('Deploy') {			
			steps { bat "docker build -t auth-img ."			    
			            bat "docker run -p 9761:8761 -d --name auth-cntr --network my-net auth-img"}		
		}		
	}
}