pipeline
{
    agent {
        label 'OneS'
    }
    
    environment {
        envString = 'true'
    }
 
    post {
        always {
            allure includeProperties: false, jdk: '', results: [[path: 'out/syntax-check/allure'], [path: 'out/smoke/allure'], [path: 'build/allure'], [path: 'build/tests/allure']]
            junit allowEmptyResults: true, testResults: 'out/syntax-check/junit/junit.xml'
            junit allowEmptyResults: true, testResults: 'out/junitreport/*.xml'
            junit allowEmptyResults: true, testResults: 'out/smoke/junit/*.xml'
            junit allowEmptyResults: true, testResults: 'build/tests/junit/*.xml'
        }
    
        failure {
            bat "echo failure"
        }
        
        success {
            bat "echo success"      
        }
    }
    stages {
//        stage("Init test IB") {
//            steps {
//                bat "chcp 65001 \n vrunner init-dev --dt D:/Dev/DT/1Cv8.dt"
// 
//            }
//        }
        stage("Smoke test") {
            steps {
                script{
                    try {
                        bat "chcp 65001\n runner xunit"
                    } catch(Exception Exc) {
                         currentBuild.result = 'UNSTABLE'
                    }
                }
 
            }
        }

    
    }
}
