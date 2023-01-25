pipeline {
	agent any 
	//agent { docker { image 'maven:3.6.3'} }
	stages{
		stage('Build') {
			steps{
				//sh "mvn --version"
				echo "Build"
				echo "$PATH"
				echo "BUILD_NUMBER - $env.BUILD_NUMBER"
				echo "BUILD JOB - $env.JOB_NAME"
				echo "BUILD TAG - $env.BUILD_TAG"
				echo "BUILD URL - $env.BUILD_URL"
			
			}
		}

		stage('Test') {
			steps{
				
				echo "Test"
		
			}
		}

		stage('Integration test') {
			steps{
			
				echo "Integration test"
			}
		}	
	}
	post{
		always{
			echo "Siempre corre"
		}
		success{
			echo "Corro cuando todo esta correcto"
		}
		failure{
			echo "Corro cuando algo sale mal"
		}
	}
}
