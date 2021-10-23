String getParalellWorkspace(WorkDirectory,specificTestName,env_input) {
    def workspace_var = "$WorkDirectory"+"\\"+"NO_"+env_input.BUILD_ID+"\\"+specificTestName
    return workspace_var+"-"+env_input.EXECUTOR_NUMBER
}

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
				echo "te"
			}
		}
	}
}
				
