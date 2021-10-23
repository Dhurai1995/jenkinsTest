// Create Jenkins job to run motion estimator tests.
// This is a scripted pipeline.


def matlab(input, term = 'exit(0)',logfile) {
    def matlabCom="\"C:/Program Files/MATLAB/R2020a/bin/matlab.exe\""
    // Wrap the code in try-catch so the code
    // always atleast has a chance to exit.
    return bat(label:"Execute Matlab Tests", script:"$matlabCom -wait -logfile $logfile -batch \"try; $input; catch e; disp(e.getReport()); exit(1); end; $term;\"&&(echo 'Success')||(echo 'Failure' && exit 1)")
}

String determineRepoName() {
    return scm.getUserRemoteConfigs()[0].getUrl().tokenize('/').last().split("\\.")[0]
}

// Returns true if there are changes in dirs
def changes_in(String... dirs) {
    def out = sh(script: "git diff --name-only origin/master ${dirs.join(' ')}",
                 returnStdout: true)
    return !out.trim().isEmpty()
}


def checkoutFullHelp(workSp) {
checkout scm
	bat(label:"Sync Git Submodule", script:"cd $workSp"+"&&git submodule sync")
    dir ('vmm_full') {
        checkout([$class: 'GitSCM', branches: [[name: '431d00a4f7b']],
            userRemoteConfigs: [[url: '']]])
    }
}

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
            environment {
                testFolder="unit_dev"
                def parallelWorkspace=getParalellWorkspace(pwd(),testFolder,env)
            }
            steps {
                echo parallelWorkspace
           }
        }
    }
}

