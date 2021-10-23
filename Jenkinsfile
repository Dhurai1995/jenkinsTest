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
            }
            steps {
                echo 'ParallelWorkspace'
                echo testFolder
                }
           }
        }
    }
}
