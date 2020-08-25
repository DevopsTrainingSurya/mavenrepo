pipeline{
agent{label 'jenkinsslave1'}
stages{
stage('Checkout-SCM'){
steps{
git branch: 'feat01', credentialsId: 'a4a241d9-5af6-4fb2-9e96-5cbb5dc20395', url: 'https://github.com/DevopsTrainingSurya/mavenrepo.git'
     }
		     }
stage('Package'){
steps{
sh '/usr/local/src/apache-maven/bin/mvn package'
     }
		}
stage('Deploy'){
steps{
withSonarQubeEnv('sonarcube2'){
sh '/usr/local/src/apache-maven/bin/mvn sonar:sonar'
			 }
     }
	       }
stage('Tomcat'){
steps{
sh 'scp /root/workspace/maven1/target/studentapp-2.1.3-FEAT01-SNAPSHOT.war root@34.214.179.8:/var/lib/tomcat/webapps'
     }
	       }
      }
	}
