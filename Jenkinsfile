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
        retry(3)
        buildDiscarder(logRotator(numToKeepStr: '5'))
    }
    stages{
        stage("Checkout code"){
            steps{
                echo "========git checkout code ========"
            }
        
        }
        stage("Build"){
            steps{
                echo "======== Install npm modules ========"
                 sh 'npm install'
                 sh 'npm cypress install'
            }
        }
        stage("Test"){
            steps{
                echo "======== Start Cypress tests ========"
                sh 'npm run test'
            }
        }
    }
    post{
        always{
            echo "======== Generate Cypress Report ========"
        }
        success{
            echo "========pipeline executed successfully ========"
        }
        failure{
            echo "========pipeline execution failed========"
        }
    }
}