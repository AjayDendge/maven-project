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
stage("Compile code")
  {
   steps
    {
      withMaven(jdk: 'java', maven: 'maven') {
     sh 'mvn compile'
    }
    }
  }
  
  stage("test code")
  {
   steps
    {
      withMaven(jdk: 'java', maven: 'maven') {
     sh 'mvn test'
    }
    }
  }
  
  stage("job Build")
  {
   steps
    {
      withMaven(jdk: 'java', maven: 'maven') {
     sh 'mvn clean package'
    }
    }
  }

 stage("Deploy on war file on tomact/dev")
  {
   steps
    {
     sshagent(['deploytomcat']) {
     sh 'scp -o StrictHostKeyChecking=no */target/*.war ec2-user@52.66.202.129:/var/lib/tomcat/webapps' 
    }
    }
  }


}
}
