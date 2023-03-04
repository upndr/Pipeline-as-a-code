pipeline {
    agent any
    environment {
        name = 'upendra'
    }
    parameters {
        string(name : 'person', defaultValue: 'Nandan Bajpai', description: "who are you?")
        booleanParam(name : 'isMale', defaultValue: true, description: "")
        choice(name : 'City', choices: ['Jaipur', 'Mumbai', 'Pune'], description: "")
    }

    stages {
        stage('Run a command') {
            steps {
                sh '''
                ls
                pwd
                date
                '''
                sh 'echo "${name}"'
            }
        }
        stage('environment variables') {
            environment {
                username = 'nandan'
            }
            steps {
                sh 'echo "${BUILD_ID}"'
                sh 'echo "${name}"'
                sh 'echo "${username}"'
            }
        }
        stage('Parameters') {
            steps {
                echo 'Deploy on test'
                sh 'echo "${name}"'
                sh 'echo "${person}"'
            }
        }
        stage('Continue ?') {
            input {
                message "should we continue?"
                ok "yes we should"
            }
            steps {
                echo 'Deploy on Prod'
                sh 'echo "{username}"'
            }
        }
    }
    post { 
        always { 
            echo 'I will always say Hello again!'
        }
        failure { 
            echo 'failure'
        }
        success { 
            echo 'success'
        }
    }
}
