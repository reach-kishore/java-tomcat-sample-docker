pipeline {
    agent any
    stages {
        stage('Build Application') {
            steps {
                bat 'mvn clean package'
            }
            post {
                success {
                    echo "Now Archiving the Artifacts...."
                    archiveArtifacts artifacts: '**/*.war'
                }
            }
        }
		stage('Create tomcat docker image'){
			steps{
			    bat 'docker build . -t tomcatsamplewebapp:${env.BUILD_ID}'
			}
		}       
    }
}