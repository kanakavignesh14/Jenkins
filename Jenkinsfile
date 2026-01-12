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
        timeout(time: 10, unit: 'SECONDS') 
        disableConcurrentBuilds() 
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
                        #sleep 10     
                        
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
        aborted {
            echo "pipeline is aborted"
        }
    }
}