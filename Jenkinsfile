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
				sh 'mvn clean install'
			}
		}
	}
}
