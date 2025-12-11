pipeline {
    agent any

    tools {
        maven 'M398'
    }

    stages {
        stage('Echo Version') {
            steps {
                bat 'echo Print Maven Version'
                bat 'mvn -version'
            }
        }

        stage('Build') {
            steps {
                git branch: 'master', url: 'https://github.com/vanessamaldonado/Jenkins-practica09'
                bat 'mvn clean package -DskipTests=true'
                archiveArtifacts 'target/hello-demo.jar'
            }
        }

        stage('Unit Test') {
            steps {
                bat 'mvn test'
                junit(testResults: 'target/surefire-reports/TEST-*.xml',
                      keepProperties: true,
                      keepTestNames: true)
            }
        }
    }
}
