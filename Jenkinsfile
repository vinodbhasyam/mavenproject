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
		archiveArtifacts artifacts:"**/*.war"
		}
		}
		}
		stage('Static Code Analysis')
		{
			steps{
			sh 'mvn checkstyle:checkstyle'
			}
		}
	}

}
