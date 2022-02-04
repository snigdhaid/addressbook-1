pipeline{
    agent any
    parameters{
        string(name: 'VERSION',defaultvalue:"",description: 'version to deploy')
        choice(name: 'VERSION',choices:['1.1.0','1.2.0','1.3.0'])
        booleanparam(name: 'executeTests',defaultvalue: true,description:"Testcases")
    }
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
            when{
                expression{
                    params.executeTests == true
                }
            }
            steps{
                script{
                    echo"package the code ${NEW_VERSION}"
                }
            }
        }
    }    
}    