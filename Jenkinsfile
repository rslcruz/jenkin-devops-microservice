pipeline {
	//agent any 
	agent { docker { image 'maven:3.6.3'} }
	stages{
		stage('Build') {
			steps{
				sh "mvn --version"
				echo "Build"
			
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
