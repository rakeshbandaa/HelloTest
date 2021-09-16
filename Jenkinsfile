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
        
      
    }
	}
