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
          withMaven(jdk: 'Java', maven: 'maven') {
  sh 'mvn package'
         }
       }
   }
 
  
  stage("docker build image")
  {
    steps{
    sh 'docker build -t ajaydendge/ci-cd:02 .'
    }
  }
  
    stage("docker image push")
  {
     steps{
    withCredentials([usernameColonPassword(credentialsId: 'dockerhub', variable: 'dockerhub')]) { 
   sh 'docker push ajaydendge/ci-cd:02'
    }
  }
  }
    
    }
  }



