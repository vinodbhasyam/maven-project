pipeline{
	agent any
	stages{
	stage('Build')
	{
	
	steps
	{
		sh 'mvn clean package'
	}
	post{
		success{
		 sh 'echo package built successfully'	
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
