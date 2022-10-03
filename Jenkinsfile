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
				sh 'mvn install -DskipTests'
			}
			}
		}
	}
}
