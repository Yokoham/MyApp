pipeline {
    agent any
    tools { maven 'Maven3' }

    stages {
        stage('Build') {
            steps { sh 'mvn clean package' }
        }
        stage('Deploy to Tomcat') {
            steps {
                deploy adapters: [tomcat9(
                    credentialsId: 'tomcat-creds',
                    path: '',
                    url: 'http://<TOMCAT_IP>:<PORT>'
                )],
                contextPath: 'myapp',
                war: 'target/*.war'
            }
        }
    }
}
