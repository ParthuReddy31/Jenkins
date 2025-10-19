pipeline {
    agent { label 'AGENT-1' }
    environment { 
        PROJECT = 'Expense'
        COMPONENT = 'Backend'
        ENV = 'prod'
        }
    options { 
        disableConcurrentBuilds() 
        timeout(time: 25, unit: 'MINUTES')
        } 
    parameters {
        string(name: 'PERSON', defaultValue: 'Parthu', description: 'Who should I say hello to?')

        text(name: 'BIOGRAPHY', defaultValue: '', description: 'I am learning to Run Jenkins Pipeline as Code')

        booleanParam(name: 'TOGGLE', defaultValue: true, description: 'Toggle this value')

        choice(name: 'CHOICE', choices: ['One', 'Two', 'Three'], description: 'Pick something')

        password(name: 'PASSWORD', defaultValue: 'SECRET', description: 'Parthu1234')
    }

    stages {
        stage('Build'){
            steps {
                script {
                    echo "Hello this is my first Jenkins pipeline Stage Build"
                    echo "Project Name is ${PROJECT}"
                }
            }
        }
        stage('Parallel Stages') {
            parallel {
                stage('Stage-1') {
                    steps {
                        script {
                            echo "Hello this is Stage 1 inside Parallel Stage"
                            sleep 10
                        }
                    }
                }
                stage('Stage-2') {
                    steps {
                        script {
                            echo "Hello this is Stage 2 inside Parallel Stage"
                            sleep 10
                        }
                    }
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
            // input {
            //     message "Should we continue?"
            //     ok "Yes, we should."
            //     submitter "alice,bob"
            //     parameters {
            //         string(name: 'PERSON', defaultValue: 'Mr Jenkins', description: 'Who should I say hello to?')
            //     }
            // }
            when {
                environment name: 'ENV', value: 'prod'
            }
            steps {
                script{
                    echo 'Hello this is my first Jenkins pipeline Stage Deploy'
                    echo "Environment Name is ${ENV}"
                    echo "Hello ${params.PERSON}"
                    echo "Biography: ${params.BIOGRAPHY}"
                    echo "Toggle: ${params.TOGGLE}"
                    echo "Choice: ${params.CHOICE}"
                    echo "Password: ${params.PASSWORD}"
                }
            }
        }
    }
    post { 
        always { 
            echo 'I will always say Hello again!'
        }
        //deleteDir() // Deletes the workspace
        // cleanup {
        //     cleanWs() // Deletes the workspace
        // }
        success {
            echo 'I will say Build-Hello on Success'
        }
        failure {
            echo 'I will say Failure-Hello on Failure'
        }
    }
}
