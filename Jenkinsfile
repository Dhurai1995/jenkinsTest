pipeline {
	agent none
	options {
		skipDefaultCheckout true
	}
	stages{
		stage('Unit test') {
			environment {
				testFolder = "Unit_dev"
				def parallelWorkspace = "$pwd()"
			}
			steps {
				echo parallelWorkspace
			}
		}
	}
}
				
