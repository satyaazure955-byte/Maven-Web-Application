pipeline {
    agent any
    tools{
        maven 'mavendefault'
    }
    stages {
        stage('checkout') {
            steps {
                git 'https://github.com/satyaazure955-byte/Maven-Web-Application.git'
            }
        }
        stage('Clean Build'){
            steps{
                sh 'mvn clean package -DskipTest=true'
            }
        }
       
         
        }
         post {

        success {
            echo 'Build Trigger Application deployed successfully'
        }

        failure {
            echo 'Pipeline failed'
        }

        always {
            cleanWs()
        }
    }
}
