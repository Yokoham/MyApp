pipeline {
    agent any
    tools { maven 'Maven3' }
    stages {
        stage('Checkout') {
            steps { checkout scm }
        }
        stage('Build') {
            steps { sh 'mvn clean package' }
        }
        stage('Deploy to Tomcat') {
            steps {
                deploy adapters: [tomcat9(credentialsId: 'tomcat-creds',
                                          path: '',
                                          url: 'http://172.31.25.95:8080')],
                       contextPath: 'myapp',
                       war: 'target/*.war'
            }
        }
    }
}
