pipeline {
	agent none
	options {
		skipDefaultCheckout true
	}
	stages{
		stage('Unit test') {
			environment {
				testFolder = "Unit_dev"
				def parallelWorkspace = dir()
			}
			steps {
				echo parallelWorkspace
			}
		}
	}
}
				
