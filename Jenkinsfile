pipeline{
    agent any
    tools {
        nodejs "nodejs24"
    }
    environment {
        NODE_HOME = tool 'nodejs24'
        PATH = "${NODE_HOME}/bin:${env.PATH}"
       // CYPRESS_CACHE_FOLDER = "/var/jenkins_home/.cache/Cypress"
        //CYPRESS_RUN_BINARY = "/var/jenkins_home/workspace/cypress2/node_modules/cypress/bin/cypress"
    }
    stages{
        stage("Enviornment Variables"){
            steps{
                echo "======== Enviornment Variables ========"
                script{
                    def pwd = pwd()
                    echo "======== Print Environment Variables ========"
                    echo "NODE_HOME: ${NODE_HOME}"
                    echo "PATH: ${PATH}"
                  //  echo "CYPRESS_CACHE_FOLDER: ${CYPRESS_CACHE_FOLDER}"
                   // echo "CYPRESS_RUN_BINARY: ${CYPRESS_RUN_BINARY}"
                    echo "WORKSPACE: ${WORKSPACE}"
                    echo "pwd: ${pwd}"
                    echo "JENKINS_HOME: ${JENKINS_HOME}"
                }
            }
        }
        stage("Install NPM"){
            steps{
                echo "======== Install npm modules ========"
                sh 'npm install'
                sh 'npm install cypress --save-dev'
            }
        }
        stage("Test"){
            steps{
                echo "======== Start Cypress tests ========"
                sh 'npm run test'
            }
        }
    }
}