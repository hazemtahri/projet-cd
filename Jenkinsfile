
pipeline {

	agent any

	stages {
		
		stage('Git ') {
            steps {
                echo 'pulling Main Project from git ...';
                git branch: 'main', credentialsId: 'git', url: 'https://github.com/amineturki/projet-cd.git'            }
        }
    
  /*     stage('Docker Build and Push') {
       steps {
         withDockerRegistry([credentialsId: "docker-hub", url: ""]) {
           sh 'sudo docker build -t amineturki/cd:latest .'
           sh 'docker push amineturki/cd:latest '
         }
       }
     }
	 */
	 	stage('Ansible playbook for test') {
            steps {
                sh 'ansible-playbook playbook-test.yml'
                         }
        }
     	
    
    node {

    env.NODEJS_HOME = "${tool 'NodeJsv12.16.2'}"
    env.PATH="${env.NODEJS_HOME}/bin:${env.PATH}"
    sh 'npm --version'

stage('Ansible playbook for building the app') {
            steps {
                sh 'ansible-playbook ansible/build.yml -i ansible/inventory/hosts.yml'
                         }
        }
}
	 
	}
	}
