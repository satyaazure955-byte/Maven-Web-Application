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
                sh 'mvn clean package'
            }
        }
       
          stage('Deploy to Tomcat') {
            steps {

                deploy adapters: [
                    tomcat9(
                        credentialsId: 'tomcat',
                        path: '',
                        url: 'http://34.170.122.223:9001'
                    )
                ],
                contextPath: 'Maven-Web-Application',
                war: '**/target/*.war'
            }
        }
        }
         post {

        success {
            echo 'Application deployed successfully'
        }

        failure {
            echo 'Pipeline failed'
        }

        always {
            cleanWs()
        }
    }
}
