pipeline{
    agent any
    environment{
        NEW_VERSION='1.3.0'
    }
    stages{
        stage("compile"){
            steps{
                script{
                    echo "compiling the code"
                }
            }
        }
        stage("test"){
            steps{
                script{
                    echo "test the code"
                }
            }
            post{
                always{
                    echo "test is completed"
                }
            }
        }
        stage("package"){
            steps{
                script{
                    echo"package the code ${NEW_VERSION}"
                }
            }
        }
    }    
}    