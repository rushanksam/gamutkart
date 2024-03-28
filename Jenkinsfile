pipeline {
    agent any
    tools {
        maven 'maven3'
    }

    stages {
        stage('Clone-Repo') {
	    	steps {
	            git branch: 'master', url: 'https://github.com/rushanksam/gamutkart.git'
	    	}
        }
	stage('Build') {
		steps {
			sh 'mvn install'
		}
	}	
 
	stage ('Compile'){
	        steps {
			sh 'mvn clean compile'
                }
	}

	stage('Run Tests') {
	    steps {
	       sh 'mvn test'
	    }
	}

        stage('Package as WAR') {
            steps {
                sh 'mvn package'
            }
        }
	stage('Deployment') {
	   steps {
		sh 'sshpass -p staragile scp target/gamutkart.war staragile@172.31.44.167:/home/staragile/apache-tomcat-9.0.85/webapps/'
	}
    }
}
}
