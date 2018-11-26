pipeline{
agent any
tools
{
	maven 'JMS_Maven'
}
parameters{
string (name:'tomcat-staging', defaultValue:'18.130.126.122', description:'Staging Server')
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
	stage('Deploy to Staging')
	{
		steps{
			 
			 sh "scp -i /var/lib/jenkins/tomcat-demo.pem **/target/*.war ec2-user@${params.tomcat-staging}:/var/lib/tomcat8/webapps"

		}
	}
}
}
