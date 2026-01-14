pipeline {
    agent {
        node {
            label 'AGENT-1'
        }
    }

    environment {
        COURSE = "jenkins"
    }

    options {
        timeout(time: 10, unit: 'SECONDS')   // pipeline max runtime
        disableConcurrentBuilds()            // prevent parallel runs
    }

    stages {
        stage('Build') {
            steps {
                script {
                    sh """ 
                        echo "Building"
                        env
                    """    
                }
            }
        }

        stage('Test') {
            steps {
                script {
                    sh """ 
                        echo "Testing"
                        echo \$COURSE
                    """    
                }
            }
        }

        stage('Deploy') {
            input {
                message "Should we continue?"
                ok "Yes, we should."
                submitter "alice,bob"
                parameters {
                    string(
                        name: 'PERSON',
                        defaultValue: 'Mr Jenkins',
                        description: 'Who should I say hello to?'
                    )
                }
            }
            steps {
                echo "Deploying"
                cleanWs()
            }
        }
    }

    post {
        always {
            echo "i will come always... HELLO WORLD"
        }
        success {
            echo "I will run if success"
        }
        failure {
            echo "I will run if failure"
        }
        aborted {
            echo "pipeline is aborted"
        }
    }
}
