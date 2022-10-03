pipeline{
	agent{
		label{
			label'built-in'
			customWorkspace'/mnt/gitrepo/'
		}
	}
	stages{
		stage('build war'){
			steps{
				sh 'mvn install -DskipTests'
			}
		}
	}
}
