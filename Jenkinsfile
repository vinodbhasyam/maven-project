pipeline{
agent any
tools{
	maven 'JMS_Maven'
     }
stages 
	{
        stage('Build') 
		{
            steps 
			{
                sh 'mvn clean package'
            }
			post 
			{
				success
				{
					echo 'Now Archiving!!'
					archiveArtifacts artifacts: '**/target/*.war'
				}
			}
        }
		
		stage('Deploy to Staging')
		{
			steps
			{
				build job:'deploy-to-staging'
			}
		}
		stage('Deploy to Production')
		{
			steps{
			timeOut(time:5,unit:'DAYS'){
			input message:'Approve Production Deployment?'
			}
			build job:'deploy-to-production'
			}
			post
			{
				success{
				echo 'Production Deployment :: Success !!'
				}
				failure{
				echo 'Production Deployment :: Failed !!'
				}
			}
		}
    }
}
