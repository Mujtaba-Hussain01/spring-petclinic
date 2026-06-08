pipeline {
    agent {
        label 'SPC'
    }
    triggers {
        pollSCM('* * * *')
    }
    stages {
        stage('git Checkout') {
            steps {
                git url: 'https://github.com/Mujtaba-Hussain01/spring-petclinic.git',
                    branch: 'main'
            }
        }
        stage('Build and scan') {
            steps {
                withSonarQubeEnv('sonar') {
                    sh 'mvn clean package sonar:sonar'
                }
            }
        }
    }
}
