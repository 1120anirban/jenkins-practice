pipeline {
    agent any
    stages {
        stage('Test') {
            steps {
                timeout(time: 3, unit: 'MINUTES') {
                    retry(3) {
                        sh './sampleBashScripts/flakey-deploy.sh'
                    }
                }
                timeout(time: 3, unit: 'MINUTES') {
                    sh './sampleBashScripts/health-check.sh'
                }
            }
        }
        stage('Sanity check') {
            steps {
                input "Does the staging environment look ok?"
            }
        }
        stage('Deploy - Production') {
            steps {
                sh './sampleBashScripts/health-check.sh'
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
