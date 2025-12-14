pipeline {
    agent any

    tools {
        maven 'mymaven'
    }

    parameters {
        choice(name: 'ENV', choices: ['Dev', 'QA'], description: 'Select environment')
    }

    stages {
        stage('Build on Dev') {
            when {
                expression { params.ENV == 'Dev' }
            }
            steps {
                git 'https://github.com/Sonal0409/DevOpsCodeDemo.git'
                sh 'mvn clean package'
            }
        }

        stage('Test on QA') {
            when {
                expression { params.ENV == 'QA' }
            }
            steps {
                git 'https://github.com/Sonal0409/DevOpsCodeDemo.git'
                sh 'mvn pmd:pmd'
                sh 'mvn test'
            }
        }
    }
}