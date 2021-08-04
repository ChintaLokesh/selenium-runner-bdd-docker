pipeline
{
   agent any 
   stages
   {
     stage("pull the latest Image")
	   {
            steps
		   {
			   sh "docker pull chintalokesh/selenium-docker-bdd"
		   }   
	   }
     stage("Start the Grid")
	 {
	   steps
	   {
	     sh "docker-compose up -d hub chrome"
	   }
	 }
     stage("Run Test")
	 {
	   steps 
	   {
	     sh "docker-compose up bdd"
	   }
	 }
   }
	post{
		always{
			archiveArtifacts artifacts: 'output/**'
			sh "docker-compose down"
		}
	}
   
}