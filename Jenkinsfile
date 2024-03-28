pipeline {
    agent {
        node {
            label "slave"
        }
     }
 
    tools {
        maven 'maven3' 
    }
    stages {
        stage ('Git Repo') {
            steps {
               git branch: 'main', credentialsId: 'git', url: 'https://github.com/rushanksam/maven.git'
            }
        }
        stage ('compile') {
            steps {
                sh 'mvn clean compile'
            }
        }
        stage ('test') {
            steps {
                sh 'mvn test'
            }
        }
        stage ('Build') {
            steps {
                sh 'mvn package'
            }
        }
        stage ('Deploy') {
            steps {
                deploy adapters: [tomcat9(credentialsId: 'tomcat', path: '', url: 'http://52.13.16.69:8080/')], contextPath: 'login', war: '**/*.war'
            }
        }
    }
}
}
}
