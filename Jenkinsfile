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
    sh 'docker build -t ajaydendge/newimage:02 .'
    }
  }
  
  stage('Push Docker Image') {
    steps{
     sh 'docker login -u "ajaydendge" -p "Ajay@9696" docker.io'
     sh 'docker push ajaydendge/newimage:02'
       }
    }
    
    }
  }



