pipeline{
	agent any
	tools{
	maven 'JMS_Maven'
	}
	stages{
	stage('Build')
	{
	
	steps
	{
		sh 'mvn clean package'
	}
	post{
		success{
		 sh 'mvn checkstyle:checkstyle'
		 publishIssues issues:[checkstyle]
		 archiveArtifacts artifacts:'**/*.war'	
		}
	}
	}
	stage('Deploy')
	{
	steps{
		sh 'echo Hello World2!!'
		}
	}
	}
}
