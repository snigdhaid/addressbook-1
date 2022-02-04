pipeline{
    agent any
    tools{
        maven 'my maven'
        jdk 'my java'
    }
    stages{
        stage("compile"){
            steps{
                script{
                    echo "compiling the code"
                    sh 'mvn compile'
                }
            }
        }
        stage("test"){
            steps{
                script{
                    echo "test the code"
                    sh 'mvn test'
                }
            }
            post{
                always{
                    junit 'target/surefire-reports/*.xml'
                }
            }
        }
        stage("package"){
            steps{
                script{
                    echo"package the code"
                    sh 'mvn package'
                }
            }
        }
        stage("Deploy"){
            when{
                expression{
                    BRANCH_NAME =='master'
                }
            }
            steps{
                script{
                    echo"Deploy the app"
                    
                }
            }
        }
    }    
}    