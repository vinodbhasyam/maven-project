pipeline{
agent any
parameters{
string (name:'tomcat-staging', defaultValue:'', description:'')
}
triggers{
pollSCM('* * * * *')
}
stages{
	stage('Build')
	{
		steps{
			sh 'mvn clean build'
			archiveartifacts artifacts:'**/targets/*.war'
		}
		post
		{
		  success
		  {
			echo 'package created'
		  }
		}
	}
}
}
