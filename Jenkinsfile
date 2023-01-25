pipeline {
	agent any 
	//agent { docker { image 'maven:3.6.3'} }

	environment{
		dockerHome = tool 'Mydocker'
		mavenHome  = tool 'myMaven'
		PATH       = "$dockerHome/bin:$mavenHome/bin:$PATH"

	}
	stages{
		stage('checkOut') {
			steps{
				sh "mvn --version"
				sh "docker version "
				echo "Build"
				echo "$PATH"
				echo "BUILD_NUMBER - $env.BUILD_NUMBER"
				echo "BUILD JOB - $env.JOB_NAME"
				echo "BUILD TAG - $env.BUILD_TAG"
				echo "BUILD URL - $env.BUILD_URL"
			
			}
		}

		stage('Build') {
			steps{
				
				sh "mvn test"		
			}
		}

		stage('Integration test') {
			steps{
				sh "mvn failsafe:integration-test failsafe:verify"
			}
		}

		stage('Package') {
			steps{
				sh "mvn package -DskipTests"
			}
		}

		stage('Build Docker image') {
			steps{
				//docker build -t raymundocruz9131/test:$env.BUILD_TAG
				script{
					dockerImage = docker.build("raymundocruz9131/test:${env.BUILD_TAG}")
				}
			}
		}	

		stage('Push Docker Image'){
			steps{
				script{
					docker.withRegistry ('','dockerhub') {
					dockerImage.push();
				    dockerImage.push('latest');
				    }
				}
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
