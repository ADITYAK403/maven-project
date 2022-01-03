pipeline
{
agent any
stages
{ 
 
 stage('scm checkout')
 { steps { git branch: 'master', url: 'https://github.com/ADITYAK403/maven-project.git' } }


 stage ('run unit test framework')
 { steps { withMaven(jdk: 'JAVA_HOME', maven: 'MAVEN_HOME') 
   {
    sh 'mvn test'
    }
 } }

  stage ('create package')
 { steps { withMaven(jdk: 'JAVA_HOME', maven: 'MAVEN_HOME') 
   {
    sh 'mvn package'
    }
 } }
 stage ('deploy to tomcat')
 {steps
  {
   sshagent(['tomcat-ssh'])
   {
    sh 'scp -o StrictHostKeyChecking=no **/*.war ec2-user@172.31.23.65:/var/lib/tomcat/webapps'}
  }
 }
  


}
}
