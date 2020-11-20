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

 stage("maven pakage ")
  {
    steps{
      withMaven(jdk: 'java', maven: 'maven')
         {
  sh 'mvn clean package sonar:sonar'
         }
       }
   }
  
    
    }
  }



