pipeline {
    agent any 
    stages {
        stage('Example Build') {
		steps{
		checkout([$class: 'GitSCM', branches: [[name: '*/master']], extensions: [], userRemoteConfigs: [[credentialsId: 'cba3c2d2-5479-4f95-b142-704670a4d890', url: 'https://github.com/CTL-DevOps/HelloTest.git']]])
            }
        }
        stage('build') {
            steps {
               bat "mvn clean install"
            }
        }
        
        stage("sonar build"){
            steps{
                bat "mvn sonar:sonar"
            }
        }
        
        stage("nexus"){
            steps{
                bat "mvn clean deploy -P release"
            }
        }
        stage("deploy to container"){
            steps{
                deploy adapters: [tomcat9(credentialsId: 'bf6f41cc-a041-4d9f-ba7d-7e3f791dde53', path: '', url: 'http://localhost:1111/')], contextPath: 'HelloTest', war: '**/*.war'
            }
        }
    }
	}