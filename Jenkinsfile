pipeline {
    agent any
    stages {
        stage('Checkout form git') {
            steps {
                git branch: 'prod' , url: 'https://github.com/Dhyey-dc0809/bootcamp1.git'
            }
        }
        stage('Complie with maven') {
            steps {
                sh 'mvn validate'
            }
        }
    }
}