pipeline{
    agent any
    tools {nodejs "node"}
    stages{
        stage("Build"){
            steps{
                echo "========executing ========"
               
            }
        
        }
        stage("Test"){
            steps{
                echo "========B executing ========"
                sh 'npm install'
                sh 'npm run test'

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