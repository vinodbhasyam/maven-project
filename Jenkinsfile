pipeline{
agent any
tools{
	maven 'JMS_Maven'
     }
parameters{
string (name:'tomcat-staging', defaultValue:'', description:'')
}
triggers{
pollSCM('* * * * *')
}
stages{
	stage('build')
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
