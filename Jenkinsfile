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
  stage("job Build")
  {
   steps
    {
      withMaven(jdk: 'java', maven: 'maven') {
     sh 'mvn package'
    }
    }
  }
}
}
