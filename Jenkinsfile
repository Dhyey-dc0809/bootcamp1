pipeline {
    agent any
    stages {
        stage('Checkout form git') {
            steps {
                git branch: 'prod' , url: 'https://github.com/Dhyey-dc0809/bootcamp1.git'
            }
        }
        stage('Validate with Maven') {
            steps {
                sh 'mvn validate'
            }
        }
        stage('Compile with Maven') {
            steps {
                sh 'mvn compile'
            }
        }
        stage('Sonar Analysis') {
            environment {
                SCANNER_HOME = tool 'sonar-scanner'
            }
            steps{
                withSonarQubeEnv('sonarserver') {
                    sh '''
                    ${SCANNER_HOME}/bin/sonar-scanner \
                    -Dsonar.organization=dhyey-dc0809 \
                    -Dsonar.projectName=mynewjavaapp \
                    -Dsonar.projectKey=mynewjavaapp \
                    -Dsonar.java.binaries=.\
                    '''
                }
            }
        }
    }
}