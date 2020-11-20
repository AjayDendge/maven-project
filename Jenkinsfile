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
    sh  'docker build -t ajaydendge/ci-cd .'
    }
  }
  
    stage("docker image push")
  {
    withCredentials([usernameColonPassword(credentialsId: 'dockerhub', variable: 'dockerhub')]) {
    steps{
    sh  'docker push ajaydendge/ci-cd'
    }
  }
  }
    
    }
  }



