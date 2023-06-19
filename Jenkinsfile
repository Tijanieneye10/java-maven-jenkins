pipeline {
    agent any
    stages {
        stage("test") {
            steps {
                echo "Running a test here..."
            }
        }

        stage("build") {
            when{
                expression {
                    BRANCH_NAME == 'main'
                }
            }

            steps {
                echo "This is running cus you are in branch $BRANCH_NAME"
            }
        }

        stage("build"){
             when{
                expression {
                    BRANCH_NAME == 'main'
                }
            }

            steps {
                echo "I can build cus of my branch"
            }
        }
    }
}