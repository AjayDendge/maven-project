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
     sh 'mvn package'
    }
    }
  }

 stage("Deploy on war file on tomact/dev")
  {
   steps
    {
   deploy adapters: [tomcat7(credentialsId: '957e2f5e-80e6-48a9-803e-3481ebb2f0f7', path: '', url: 'http://52.66.202.129:8080/')], contextPath: null, war: '**/*.war'
    
    }
  }


}
}
