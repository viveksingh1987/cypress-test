pipeline{
    agent {
         docker {
            image 'node:22' // or any other version you need
            args '-v /var/run/docker.sock:/var/run/docker.sock' // if you need Docker-in-Docker
          }
    }
    stages{
        stage("Build"){
            steps{
                echo "========executing ========"
               
            }
            post{
                always{
                    echo "========always========"
                }
                success{
                    echo "========A executed successfully========"
                }
                failure{
                    echo "========A execution failed========"
                }
            }
        }
        stage("Test"){
            steps{
                echo "========B executing ========"
                sh 'npm install'
                sh 'npm run test'

            }
            post{
                always{
                    echo "========always========"
                }
                success{
                    echo "========B executed successfully========"
                }
                failure{
                    echo "========B execution failed========"
                }
            }
        }
    }
    post{
        always{
            echo "========always========"
        }
        success{
            echo "========pipeline executed successfully ========"
        }
        failure{
            echo "========pipeline execution failed========"
        }
    }
}