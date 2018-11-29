pipeline{
	agent any
	tools
	{
	maven 'JMS_Maven'
	}
	triggers{
	scm('H/5 * * * *')
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
			post{
			success{
				checkstyle canComputeNew: false, defaultEncoding: '', healthy: '', pattern: '', unHealthy: ''
			}
			}
		}
	}

}
