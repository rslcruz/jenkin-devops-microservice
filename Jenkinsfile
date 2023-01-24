pipeline {
	agent any 
	stages{
		stage('Build') {
			steps{
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
