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
    sh 'docker build -t ajaydendge:01 .'
    }
  }
  
  stage('Push Docker Image') {
    steps{
withDockerRegistry(credentialsId: 'ecr:ap-south-1:5f989864-2e73-47af-a5d2-fcb694181742', url: 'https://112631035129.dkr.ecr.ap-south-1.amazonaws.com/ajaydendge') {
   sh 'docker tag ajaydendge:01 112631035129.dkr.ecr.ap-south-1.amazonaws.com/ajaydendge:01'
   sh 'docker push 112631035129.dkr.ecr.ap-south-1.amazonaws.com/ajaydendge:01'
}}}
    
    }
  }



