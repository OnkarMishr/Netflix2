pipeline {
    agent any

    
    stages {
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
