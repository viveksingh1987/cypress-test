pipeline{
    agent any
    tools {
        nodejs "nodejs24"
    }
    environment {
        NODE_HOME = tool 'nodejs24'
        PATH = "${NODE_HOME}/bin:${env.PATH}"
    }
    options {
        disableConcurrentBuilds()
        timestamps()
        timeout(time: 1, unit: 'HOURS')
    }
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