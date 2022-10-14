pipeline {
    agent { label'jdk11' }
    triggers { pollSCM('* * * * *') }
    stages {
        stage ('clone') {
            steps {
                git url: 'https://github.com/chandushine/openmrs-core.git',
                 branch: 'master'
            }
        }
        stage ('build') {
            steps {
                sh 'mvn clean install'
            }
        }
        stage ('archive') {
            steps {
                archive '**/target/*.jar'
            }
        }
                stage ('junit') {
            steps {
                junit '**/target/surefire-reports/*.xml'
            }
        }

    }
    }
