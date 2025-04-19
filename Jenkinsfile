pipeline {
    agent any

    stages {
        stage('Clone') {
            steps {
                git credentialsId: 'Server', url: 'git@github.com:SumonT2/OSTAD-Assignment-module-3.git',branch: 'main'
            }
        }

        stage('Install') {
            steps {
                sh 'npm install'
            }
        }

        stage('Test') {
            steps {
                script {
                    try {
                        sh 'npm run check'
                    } catch (err) {
                        currentBuild.result = 'FAILURE'
                        throw err
                    }
                }
            }
        }
    }

    post {
        always {
            echo "Build finished with status: ${currentBuild.result}"
        }
    }
}
