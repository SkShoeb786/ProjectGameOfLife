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
				sh 'mvn clean install -DskipTests'
			}
		}
		stage('rm -rf slave1'){
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
				sh 'scp -i /root/sk1.pem /mnt/projects/assignment2/gameoflife-web/target/gameoflife.war ec2-user@65.2.186.89:/mnt/webserver/apache-tomcat-9.0.65/webapps/'
			}
		}
		stage('deploy on slave1'){
			agent{
				label{
					label'slave1'
					customWorkspace'/mnt/webserver/apache-tomcat-9.0.65/bin/'
				}
			}
			steps{
				sh './shutdown.sh'
				sh 'sleep 5'
				sh './startup.sh'
			}
		}
		stage('rm -rf slave2'){
			agent{
				label{
					label'slave2'
					customWorkspace'/mnt/webserver/apache-tomcat-9.0.65/webapps/'
				}
			}
			steps{
				sh 'rm -rf /mnt/webserver/apache-tomcat-9.0.65/webapps/game*'
			}
		}
		stage('copy WAR on slave2'){
			steps{
				sh 'scp -i /root/sk1.pem /mnt/projects/assignment2/gameoflife-web/target/gameoflife.war ec2-user@43.205.255.219:/mnt/webserver/apache-tomcat-9.0.65/webapps/'
			}
		}
		stage('deploy on slave2'){
			agent{
				label{
					label'slave2'
					customWorkspace'/mnt/webserver/apache-tomcat-9.0.65/bin/'
				}
			}
			steps{
				sh './shutdown.sh'
				sh 'sleep 5'
				sh './startup.sh'
			}
		}
	}
}
