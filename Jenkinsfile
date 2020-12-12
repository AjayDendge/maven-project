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
 withCredentials([[$class: 'AmazonWebServicesCredentialsBinding', accessKeyVariable: 'AWS_ACCESS_KEY_ID', credentialsId: '5f989864-2e73-47af-a5d2-fcb694181742', secretKeyVariable: 'AWS_SECRET_ACCESS_KEY']]) {
   sh 'aws ecr get-login-password --region ap-south-1 | docker login --username AWS --password-stdin 112631035129.dkr.ecr.ap-south-1.amazonaws.com'
 }}}
    
    }
  }



