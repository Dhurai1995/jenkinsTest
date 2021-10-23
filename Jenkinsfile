String getParalellWorkspace(WorkDirectory,specificTestName,env_input) {
    // Purpose of this function is to give a unique workspace name
    // Also that it needs to be short enough to run without errors with too long pathname
    // Need to shorten the path here unfortunately...
    def workspace_var = "$WorkDirectory"+"\\"+"NO_"+env_input.BUILD_ID+"\\"+specificTestName
    return workspace_var+"-"+env_input.EXECUTOR_NUMBER
}

pipeline {
    agent none
    options {
        skipDefaultCheckout true
    }
    stages {
        stage('Unit Tests') {
            agent {
                label "Matlab2020a_cxv_win"
            }
            environment {
                testFolder="unit_dev"
                def parallelWorkspace=getParalellWorkspace(pwd(),testFolder,env)
            }
            steps {
                echo 'ParallelWorkspace'
                echo parallelWorkspace
                }
           }
        }
    }
}
