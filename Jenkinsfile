pipeline 
{
    agent 
    {
      docker 
      {
          image 'maven:3-alpine'
       }  
    }
    stages 
    {
        stage('Build') 
        {
          steps 
          {
              sh 'mvn -B -DskipTests clean package'
           }
         }
         
        stage('Test') 
        {
            steps 
            {
            sh 'java -jar target/hello-world-1.jar'
            }
        }
        
        stage('PublishJira') 
        {
            steps 
            {
              junit '/Users/sannan/.jenkins/jobs/CI-Pipeline/builds/3/workflow/*.xml'
                build 'jira2'
            }
        }
     }
}
