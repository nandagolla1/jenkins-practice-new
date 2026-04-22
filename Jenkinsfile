pipeline {
    agent {
        node {
             label 'AGENT-1'
        }
    }

    environment { 
        COURSE = 'jenkins'
    }


    options {
        // Timeout counter starts AFTER agent is allocated
        timeout(time: 1, unit: 'MINUTES')
        disableConcurrentBuilds()
    }


    parameters {
        string(name: 'PERSON', defaultValue: 'Mr Jenkins', description: 'Who should I say hello to?')

        text(name: 'BIOGRAPHY', defaultValue: '', description: 'Enter some information about the person')

        booleanParam(name: 'TOGGLE', defaultValue: true, description: 'Toggle this value')

        choice(name: 'CHOICE', choices: ['One', 'Two', 'Three'], description: 'Pick something')

        password(name: 'PASSWORD', defaultValue: 'SECRET', description: 'Enter a password')
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
        }

        stage('testing') {
            steps {
                echo 'testing....'
            }
        }

        stage('deploy') {
            input {
                message "Should we continue?"
                ok "Yes, we should."
                submitter "alice,bob"
                parameters {
                    string(name: 'PERSON', defaultValue: 'Mr Jenkins', description: 'Who should I say hello to?')
                }
            }
            steps {
                script{
                    echo "Hello, ${PERSON}, nice to meet you."
                    
                    echo 'Deploying..'
                }
        }
        }

    post { 
        always { 
            echo 'I will always say Hello again!'
            deleteDir()
        }
        success { 
            echo 'Hello Success'
        }
        failure { 
            echo 'Hello Failure'
        }
    }
    }
}