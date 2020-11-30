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
    sh 'docker build -t ajaydendge/newimage:03 .'
    }
  }
  
  stage('Push Docker Image') {
    steps{
    withCredentials([usernamePassword(credentialsId: 'hub123', passwordVariable: '', usernameVariable: '')]) {
     sh 'docker push ajaydendge/newimage:03'
       }
    }}
    
    }
  }



