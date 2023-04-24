pipeline {
    agent {label 'slave'}
    stages {
    stage('branch name'){
            steps{
                    echo "${env.BRANCH_NAME}"
            } 
        }
    stage('dev') {
    agent{label 'slave'}
    when{
               allOf{
                branch "dev"
                triggeredBy cause: 'UserIdCause'
                }
            }
        stages{
            stage('get top of slave in dev build') {
                steps{
                    sh 'top -b -n 1'
                }
            }
            stage('get hostname of slave in dev build') {
                steps{
                    sh 'head -n 10 && hostname'
                }
            }
        }
    }
    }
}
