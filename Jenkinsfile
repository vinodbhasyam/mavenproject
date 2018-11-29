pipeline{
	agent any
	tools
	{
	maven 'JMS_Maven'
	}
	triggers{
	pollSCM('H/5 * * * *')
	}
	stages{
		stage('Build')
		{
		steps{
		sh 'mvn clean package'
		}
		post{
		success
		{
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
		stage('Deploy to Docker')
		{
		steps{
		  
		  sh "docker build . -t tomcatwebapp:${env.BUILD_ID}"
		  
		  }
		}
		}
	}
