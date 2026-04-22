pipeline {
    agent {
        node {
             label 'AGENT-1'
        }
    }
    options {
        // Timeout counter starts AFTER agent is allocated
        timeout(time: 1, unit: 'SECONDS')
    }
    stages {
        stage('image build') {
            steps {
                script {
                    if (env.BRANCH_NAME == 'main') {
                        sh 'echo "Main branch build"'
                    } else {
                        sh 'echo "Other branch"'
                    }
                }
            }

        stage('testing') {
            steps {
                echo 'testing....'
            }
        }

        stage('deploy') {
            steps {
                sh "echo 'deploying....'"
            }
        }
    }

    post { 
        always { 
            echo 'I will always say Hello again!'
        }
    }
}