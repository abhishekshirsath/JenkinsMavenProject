pipeline {
	agent any
	stages {
		/*
		stage("Cleaning Stage") {
			steps{
				bat "mvn clean"
			}
		}
		stage("Testing stage") {
			steps {
				//bat "mvn test"
				echo "Testing stage"
			}
		}
		stage("Packaging stage"){
			steps {
				//bat "mvn package"
				echo "Packaging stage"
			}
		}
		*/

		stage("Parallel Execution") {
			steps {
				parallel(
				      a: {
					//bat "mvn clean"
					      echo "mvn clean"
				      },
				      b: {
					//bat "mvn test"
					      echo "mvn test"
				      },
				      c: {
					//bat "mvn package"
					      echo "mvn package"
				      }
				)
			}
		}
		
		stage("Consolidate Results") {
			steps {
				input ("Do you want to capture results?")
				//junit '**/target/surefire-reports/TEST-*.xml'
				//archive 'target/*.jar'
				echo "In Consolidate Results stage"
			}
		}

		stage("Email Build Status"){
			steps {
				//mail body: "${env.JOB_NAME}  - Build # ${env.BUILD_NUMBER}  - ${currentBuild.currentResult} \n\nCheck console output at ${env.BUILD_URL} to view the results.", subject: "${env.JOB_NAME}  - Build # ${env.BUILD_NUMBER}  - ${currentBuild.currentResult}!!", to: 'abhishekshirsath289@gmail.com'
				mail bcc: '', body: 'Sample body', cc: '', from: '', replyTo: '', subject: 'Sample subject', to: 'abhishekshirsath289@gmail.com'
			}
		}
	}
}
