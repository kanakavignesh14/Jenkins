pipeline {
    agent {
       node {
           label 'AGENT-1'
        
       }
    }

    environment {
        COURSE = "jenkins"
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
                        echo "Building"
                        echo $COURSE        
                        
                    """    
                }
                
            }
        }
        stage('Deploy') {
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
    }
}