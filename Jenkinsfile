pipeline{
	agent any
	tools
	{
	maven 'JMS_Maven'
	}
	stages{
		stage('Build'){
		steps{
		sh 'mvn clean package'
		}
		post{
		success{
		archiveArtifacts artifact:"**/*.war"
		}

		}
		}
	}

}
