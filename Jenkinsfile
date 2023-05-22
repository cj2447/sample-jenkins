pipeline {
    agent any
    tools {
            jfrog 'jfrog-cli'
        }
    environment {
        JFROG_CLI_BUILD_NAME = "my-build-name"
        JFROG_CLI_BUILD_NUMBER = "18"
    }
    stages {  
        stage('Build') {
            steps {
                echo 'Building..'
            }
        }
        stage('Test') {
            steps {
                echo 'Testing.d.'
            }
        }
        stage('Deploy') {
            steps {
                echo 'Deploying....'
            }
        }
        stage('Testing'){
            steps {
                 // Show the installed version of JFrog CLI.
                jf '-v'
                
                // Show the configured JFrog Platform instances.
                jf 'c show'
                
                // Ping Artifactory.
                jf 'rt ping'
                
                // Create a file and upload it to a repository named 'my-repo' in Artifactory
                sh 'touch test-file'
                jf 'rt u test-file miggyrepo/'
                
                // Publish the build-info to Artifactory.
                jf 'rt bp'
            }
        }
    }
}
