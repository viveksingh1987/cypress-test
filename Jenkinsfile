pipeline{
    agent any
    tools {
        nodejs "nodejs24"
    }
    environment {
        NODE_HOME = tool 'nodejs24'
        PATH = "${NODE_HOME}/bin:${env.PATH}"
        //CYPRESS_CACHE_FOLDER = "/var/jenkins_home/workspace/cypress2/node_modules/cypress/"
        //CYPRESS_RUN_BINARY = "/var/jenkins_home/workspace/cypress2/node_modules/cypress/bin/cypress"
    }
    options {
        disableConcurrentBuilds()
        timestamps()
        timeout(time: 1, unit: 'HOURS')
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
                 //sh 'npm install'
                echo $NODE_HOME
                echo $JENKINS_HOME
                echo $WORKSPACE
                echo $pwd
            }
        }
        stage("Install Cypress"){
            // steps{
            //     echo "======== Install Cypress ========"
            //      sh 'npm install cypress --force'
            // }
                // steps{
                //     sh """
                //     echo $pwd

                //     npm install && 
                //     export NODE_TLS_REJECT_UNAUTHORIZED=0 && 
                //     ./node_modules/.bin/cypress install --force && 
                //     ./node_modules/.bin/cypress run --headless --browser chrome 
                //     """
                // }
        }
         stage("Verify Cypress"){
            steps{
                echo "======== Verify Cypress ========"
               // sh 'ls -l /var/jenkins_home/.cache/Cypress/14.3.3/Cypress'
            }
        }
        stage("Test"){
            steps{
                echo "======== Start Cypress tests ========"
                sh 'npx cypress run'
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