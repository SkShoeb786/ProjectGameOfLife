pipeline{
	agent{
		label{
			label'built-in'
			customWorkspace'/mnt/projects/assignment2'
			}
		}
	stages{
		stage('maven clean install'){
			steps{
				sh 'mvn clean install'
			}
		}
	}
}
