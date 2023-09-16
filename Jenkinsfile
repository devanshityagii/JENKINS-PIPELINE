pipeline{
	agent any
	stages{
		stage("Build"){
			steps{
				echo "Building Project with Maven"
			}
		}
		stage("Unit and Integration Tests"){
			steps{
				echo "Testing the code using JUnit"
			}
			post{
				success{
					mail to: "devanshityagi04@gmail.com",
					subject: "SUCCESS : Unit and Test Integration",
					body: "Successfully completed the unit and integration tests"
				}
			}
		}
		stage("Code Analysis"){
			steps{
				echo 'Analysing with SonarQube'
			}
		}
		stage("Security Scan"){
			steps{
				echo 'Security scanning with SonarQube'
			}
			post{
				success{
					mail to: "devanshityagi04@gmail.com",
					subject: "SUCCESS : Security Scan",
					body: "Successfully completed the security scan"
				}
			}
		
		}
		stage("Deploy To Staging Server"){
			steps{
				echo "Deploying code to AWS EC2 instance"
			}
		}
		stage("Integration Tests on Staging"){
			steps{
			echo "Running Integration tests on staging server"
			}
			post{
				success{
					mail to: "devanshityagi04@gmail.com",
					subject: "SUCCESS : Integration tests on Staging",
					body: "Successfully completed integration tests on staging"
				}
			}
		}
		stage("Deploy To Production Server"){
			steps{
				echo 'Deploying code to AWS EC2 Instance'
			}
		}
	}
	post{
		always{
			emailext attachLog: true,
			to: 'devanshityagi04@gmail.com',
			subject: "status: ${currentBuild.result}",
			body: "Status of build: ${currentBuild.result}"
		}
	}
}
