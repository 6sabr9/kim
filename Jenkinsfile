pipeline{
	agent any
	stages{

		stage("Building Stage..."){
			steps{
			sh 'mvn clean package'
			}
			post {
				success{
				echo 'Build is successful'
				}
			}
		}
		stage ("Archieving Artifacts..."){
			steps{
				archiveArtifacts artifacts: "**/*.war"
			}
			post {
				success{
				echo "Job successfully achieved..."
				}
			}
		}
		stage ("Deploy to Tomcat Container..."){
			steps{
					sh "docker build . -t tomcatwebapp:${evn.BUILD_ID}"
			}
			post{
				success{
					echo 'Successfully build and deploy to container'
				}
			}
		}
	}
}