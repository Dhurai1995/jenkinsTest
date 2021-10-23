
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
