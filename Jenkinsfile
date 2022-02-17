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
        stage("build the docker image"){
            steps{
                script{
                    echo "building the docker image"
                    sh 'sudo yum install docker -y'
                    sh 'systemctl start docker'
                    withCredentials([usernamePassword(credentialsId: 'dockerhub', passwordVariable: 'PASS', usernameVariable: 'USER')]) {
                       sh 'sudo docker build -t snigdha76/jmvn-privaterepos:$BUILD_NUMBER .' 
                       sh 'sudo docker login -u $USER -p $PASS'
                       sh 'sudo docker push snigdha76/jmvn-privaterepos:$BUILD_NUMBER'            
                    }
                }
            }
        }
        stage("Deploy the docker container"){
            steps{
                script{
                    echo "deploying the app"
                    sh 'sudo docker run -itd -P snigdha76/jmvn-privaterepos:$BUILD_NUMBER'
                }
            }
        }
    }    
}    