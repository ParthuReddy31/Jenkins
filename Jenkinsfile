pipeline {
    agent { label 'AGENT-1' }
    environment { 
        PROJECT = 'Expense'
        COMPONENT = 'Frontend'
        ENV = 'Dev'
        }
    options { 
        disableConcurrentBuilds() 
        timeout(time: 10, unit: 'SECONDS')
        } 

    stages {
        stage('Build'){
            steps {
                script {
                    echo "Hello this is my first Jenkins pipeline Stage Build"
                    echo "Project Name is ${PROJECT}"
                    sleep 30
                }
            }
        }
        stage("test"){
            steps {
                script{
                    sh """ 
                    echo "Hello this is my first Jenkins pipeline Stage Test"
                    echo "Component Name is ${COMPONENT}"
                    """
                }
            }
        }
        stage('Deploy'){
            steps {
                script{
                    echo 'Hello this is my first Jenkins pipeline Stage Deploy'
                    echo "Environment Name is ${ENV}"
                }
            }
        }
    }
    post { 
        always { 
            echo 'I will always say Hello again!'
        }
        success {
            echo 'I will say Build-Hello on Success'
        }
        failure {
            echo 'I will say Failure-Hello on Failure'
        }
    }
}
