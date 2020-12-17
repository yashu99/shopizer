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
                deploy adapters: [tomcat9(credentialsId: 'bee2845a-6f5e-468c-9dbb-673eeb19895e', path: '', url: 'http://localhost:9091')], contextPath: 'shopizer', war: '**/*.war'
            }
        }
    }
}
