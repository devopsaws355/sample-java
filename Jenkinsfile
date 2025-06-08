pipeline {
	agent any
	
	stages{
		stage('Checkout Code'){
			steps{
				git branch: 'master', url: 'https://github.com/devopsaws355/sample-java.git'
				}
			}
	
	stage('Build'){
		steps{
			sh "mvn clean install -Dmaven.test.skip=true"
		}
	}
	
	stage('Archive Artifact'){
		steps{
		archiveArtifacts artifacts:'target/*.war'
		}
	}
	
	stage('deployment'){
		steps{
		//deploy adapters: [tomcat9(credentialsId: 'TomcatCreds' path: '', url: 'http://52.90.187.236:8080/')], contextPath: 'counterwebapp', war: 'target/*.war'
		deploy adapters: [tomcat9(url: 'http://15.206.84.98:8081/', 
                              credentialsId: 'TomcatCreds')], 
                     war: 'target/*.war',
                     contextPath: 'app'
		}
		
	}
	
	// stage('Notification'){
	// 	steps{
	// 	emailext(
	// 		subject: "Job Completed",
	// 		body: "Jenkins pipeline job for maven build job completed",
	// 		to: "sudheer.baraker@gmail.com"
	// 	)
	// 	}
	// }
	}
}
