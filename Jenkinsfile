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
                    echo "dev top"
                    sh 'top -b -n 1'
                }
            }
            stage('get hostname of slave in dev build') {
                steps{
                    echo "dev host"
                    sh 'head -n 10 && hostname'
                }
            }
        }
    }
    stage('prod') {
    agent{label 'masternode || slave'}
    when{
               allOf{
                branch "prod"
                triggeredBy cause: 'UserIdCause'
                }
            }
        stages{
            stage('get top of slave in dev build') {
                steps{
                    echo "prod top"
                    sh 'top -b -n 1'
                }
            }
            stage('get hostname of slave in dev build') {
                steps{
                    echo "prod host"
                    sh 'head -n 10 && hostname'
                }
            }
        }
    }
    }
}
