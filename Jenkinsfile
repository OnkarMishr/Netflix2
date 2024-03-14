pipeline {
    agent any

    environment {
        ENVIRONMENT = 'UAT' // Set the environment variable here or you can set it dynamically
    }
    stages {
        stage('Checkout') {
	        steps {
			checkout scm			       
		      }}
        
		stage('Build') {
	           steps {
			  sh '/home/onkar/Documents/Devops_Softawre/apache-maven-3.9.6/bin/mvn install'
	                 }}
        
        stage('Deploy') {
            steps {
                script {
                    if (env.ENVIRONMENT == 'QA') {
                        sh '''
                            sshpass -p "dev" scp target/Netflix2.war grras@172.17.0.2:/home/grras/appfiles/apache-tomcat-9.0.85/webapps
                            echo "Deployment to QA environment done"
                        '''
                    } else if (env.ENVIRONMENT == 'UAT') {
                        sh '''
                            cp target/Netflix2.war /home/onkar/Documents/Devops_Softawre/apache-tomcat-9.0.85/webapps
                            echo "Deployment to UAT environment done"
                        '''
                    } else {
                        echo "Invalid environment specified"
                    }
                }
            }
        }
    }
}
