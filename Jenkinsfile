pipeline{
	agent{
		label{
			label'built-in'
			customWorkspace'/mnt/project/'
		}
	}
	stages{
		stage('build war'){
			steps{
				dir('/mnt/project/'){
				sh 'mvn clean install -DskipTests'
			}
			}
		}
		stage('slave1 clear previos war'){
			agent{
				label{
					label'slave1'
				}
			}
			steps{
				sh 'sudo rm -rf /home/ec2-user/webserver/apache-tomcat-9.0.67/webapps/*'
			}
		}
		stage('deploy gameoflife on slave1'){
			steps{
				sh 'scp -i /root/Common.pem /mnt/project/gameoflife-web/target/gameoflife.war ec2-user@13.232.227.175:/home/ec2-user/webserver/apache-tomcat-9.0.67/webapps'
			}
		}
		stage('start tomcat slave1'){
			agent{
				label{
					label'slave1'
				}
			}
			steps{
				sh 'sudo /home/ec2-user/webserver/apache-tomcat-9.0.67/bin/shutdown.sh'
				sh 'sudo /home/ec2-user/webserver/apache-tomcat-9.0.67/bin/startup.sh'
			}
		}
	}
}
