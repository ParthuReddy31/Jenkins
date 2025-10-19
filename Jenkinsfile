pipeline {
    agent { label 'AGENT-1' }
    stages {
        stage('Build'){
            steps {
                script {
                    echo "Hello this is my first Jenkins pipeline Stage Build"
                }
            }
        }
        stage("test"){
            steps {
                script{
                    sh """ 
                    echo "Hello this is my first Jenkins pipeline Stage Test"
                    """
                }
            }
        }
        stage('Deploy'){
            steps {
                script{
                    echo 'Hello this is my first Jenkins pipeline Stage Deploy'
                }
            }
        }
    }
}
