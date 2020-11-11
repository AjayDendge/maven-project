pipeline
{
agent any
stages
{
stage("SCM")
  {
  steps
  {
  git branch: 'master', url: 'https://github.com/AjayDendge/maven-project.git'
  }
  }

 stage("maven pacage with sonarqube ")
  {
   steps
    {
   withSonarQubeEnv('sonarqube') 
       {
      withMaven(jdk: 'java', maven: 'maven')
         {
     sh 'sonar:sonar package'
         }
       }
   }
  }
    
    }
  }



