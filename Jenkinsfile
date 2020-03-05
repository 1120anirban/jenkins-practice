pipeline {
    agent any /*{
        docker { image 'node:7-alpine' }
    }*/
    stages {
        stage('Build') {
            steps {
                retry(3) {
                    bat '''
                        set
                        sampleBatFiles\\sample_script.bat
                    '''
                }
                timeout(time: 2, unit: 'MINUTES') {
                    retry(2) {
                        bat 'sampleBatFiles\\timeout.bat'
                    }
                }
            }
        }
    }
    post {
        always {
            echo 'This will always run'
        }
        success {
            echo 'This will run only if successful'
        }
        failure {
            echo 'This will run only if failed'
        }
        unstable {
            echo 'This will run only if the run was marked as unstable'
        }
        changed {
            echo 'This will run only if the state of the Pipeline has changed'
            echo 'For example, if the Pipeline was previously failing but is now successful'
        }
    }
}