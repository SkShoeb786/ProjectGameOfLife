pipeline{
	agent{
		label{
			label'built-in'
			customWorkspace'/mnt/projects/assignment2'
			}
		}
		tools{
			maven 'apache-maven-3.8.6'
		}
	stages{
		stage('maven clean install'){
			steps{
				sh 'rm -rf /root/.m2/repository/*'
				sh 'mvn clean install'
			}
		}
		stage('rm -rf' slave1'){
			agent{
				label{
					label'slave1'
					customWorkspace'/mnt/webserver/apache-tomcat-9.0.65/webapps/'
				}
			}
			steps{
				sh 'rm -rf /mnt/webserver/apache-tomcat-9.0.65/webapps/game*'
			}
		}
		stage('copy WAR on slave1'){
			steps{
				sh ' scp -i /root/sk1.pem /mnt/projects/assignment2/gameoflife-web/target/gameoflife.war ec2-user@65.2.186.89:/mnt/webserver/apache-tomcat-9.0.65/webapps/
			}
		}
		
	}
}
