pipeline {
    agent {
        label 'SPC'
    }
    triggers {
        pollSCM('* * * * *')
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
                withCredentials([string(credentialsId: 'sonar_id', variable: 'SONAR_TOKEN')]) {
                    withSonarQubeEnv('SONAR') {
                        sh '''
                            mvn clean package sonar:sonar \
                                -Dsonar.projectKey=Mujtaba-Hussain01_spring-petclinic \
                                -Dsonar.organization=mujtaba-hussain01 \
                                -Dsonar.host.url=https://sonarcloud.io/ \
                                -Dsonar.login=$SONAR_TOKEN
                        '''
                    }
                }
            }
        }
        stage(Artifact Publishing) {
            steps {
                
            }
        }
    }
}
