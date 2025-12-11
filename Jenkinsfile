pipeline {
    agent any

    tools {
        maven 'M398'
    }

    stages {
        stage('Echo Version') {
            steps {
                sh 'echo Print Maven Version'
                sh 'mvn -version'
            }
        }

        stage('Build') {
            steps {
                git branch: 'main', url: 'file:///C:/ruta/a/jenkins-hello-world.git'
                sh 'mvn clean package -DskipTests=true'
                archiveArtifacts 'target/hello-demo-*.jar'
            }
        }

        stage('Unit Test') {
            steps {
                sh 'mvn test'
                junit(testResults: 'target/surefire-reports/TEST-*.xml',
                      keepProperties: true,
                      keepTestNames: true)
            }
        }
    }
}
