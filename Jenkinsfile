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
        stage("build") {
            when {
                expression {
                    params.executeTest
                }
            }
            steps {
                echo "Here is my first build ${NEW_VERSION}"
                echo "The branch am building is ${BRANCH_NAME}"
            }
        }

        stage("test") {
            
            steps {
                echo "test running..."
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
