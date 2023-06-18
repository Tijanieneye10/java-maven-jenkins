def gv 
pipeline {
    agent any
    environment {
        NEW_VERSION = "1.0.0"
    }
    parameters {
        string(name: 'VERSION', defaultValue: 'latest', description: 'Software version')
        choice(name: 'APPNAME', choices: ['laravel', 'amazon', 'azure'], description: 'Select software type')
        booleanParam(name:  'executeTest', defaultValue: true, description: 'Do you want to run test')
    }
    stages {
        stage("from groovy script"){
            steps{
                script {
                    gv = load "script.groovy"
                }
            }
        }
        
        stage("output from groovy script"){
            steps {
                script {
                    gv.buildApp()
                }
            }
        }
        stage("build") {
            when {
                expression {
                    params.executeTest
                }
            }
            steps {
                echo "Here is my first build ${NEW_VERSION}"
                echo "The branch am building is ${params.APPNAME}"
            }
        }

        stage("test") {

            input {
                message "Select your environment"
                ok "Done"
                parameters {
                    choice(name: 'ENVIRONMENT', choices: ['dev', 'staging', 'production'], description: 'Select environment')
                }
            }
            
            steps {
                echo "test running on ${ENVIRONMENT}"
                echo "test passed..."
            }
        }

        stage("deploy") {
            steps {
                echo "deploying..."
                echo "deployed"
            }
        }
    }

}
