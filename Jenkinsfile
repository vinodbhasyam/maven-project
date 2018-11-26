pipeline{
agent any
tools
{
	maven 'JMS_Maven'
}
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
			sh 'mvn clean package'
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
