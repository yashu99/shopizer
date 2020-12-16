pipeline {
    agent any
        tools {
            maven 'MAVEN_HOME'
            jdk 'JAVA_HOME'
        }
    stages {
        stage ('Build') {
            steps {
                echo "Building Project"
                bat '''
                mvn clean install
                '''
            }
        }
        stage('Test') {
            steps {
                bat '''
                 mvn -B verify
                '''
            }
        }
        stage('Deploy') {
            steps {
                echo "Deploy"
                deploy adapters: [tomcat9(credentialsId: '476ef20f-d63d-420a-aef1-4a3ddfa1a9c4', path: '', url: 'http://localhost:8080')], contextPath: 'Shopizer', war: '**/*.war'
            }
        }
    }
}
