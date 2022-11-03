
pipeline {

	agent any

	stages {
		
		stage('Git ') {
            steps {
                echo 'pulling Main Project from git ...';
                git branch: 'main', credentialsId: 'git', url: 'https://github.com/amineturki/projet-cd.git'            }
        }
    
       stage('Docker Build and Push') {
       steps {
         withDockerRegistry([credentialsId: "docker", url: ""]) {
           sh 'sudo docker build -t amineturki/cd:latest .'
           sh 'docker push amineturki/cd:latest '
         }
       }
     }
	}
	}
