pipeline{
agent any
tools
{
	maven 'JMS_Maven'
}
parameters{
string (name:'tomcat-staging', defaultValue:'18.130.126.122', description:'')
}
triggers{
pollSCM('* * * * *')
}
stages{
	stage('Build')
	{
		steps{
			sh 'mvn clean package'
			archiveArtifacts artifacts:'**/target/*.war'
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
