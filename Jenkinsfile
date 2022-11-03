
pipeline {

	agent any

	stages {
		
		stage('Git ') {
            steps {
                echo 'pulling Main Project from git ...';
                git branch: 'main', credentialsId: 'git', url: 'https://github.com/amineturki/project-cd.git'            }
        }
	}
	}
