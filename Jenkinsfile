pipeline {
    agent any
    stages {
        stage('Build') {
            steps {
              retry(3) {
                    bat '''
                           set
                           .\sampleBatFiles\sample_script.bat
                        '''
                }

                timeout(time: 3, unit: 'MINUTES') {
                    bat '.\sampleBatFiles\timeout.bat'
                }
            }
        }
    }
}