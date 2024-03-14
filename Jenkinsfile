pipeline {
    agent any
    
    environment {
        MVN_HOME = tool 'Maven'
        PATH = "$MVN_HOME/bin:$PATH"
    }
    
    stages {
        stage('Checkout') {
            steps {
                // Connect to Git repository using SCM
                checkout scm
            }
        }
        
        stage('Build') {
            steps {
                // Execute Maven install command
                sh 'mvn install'
            }
        }
    }
}
