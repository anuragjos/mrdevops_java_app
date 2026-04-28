@Library('my_shared_libraries') _

pipeline {
    agent any

    parameters {
        choice(
            name: 'action',
            choices: 'create\ndelete',
            description: 'choose create/destroy'
        )
    }

    tools {
        maven 'maven'
    }

    stages {

        stage("Git Checkout") {
            when {
                expression { params.action == 'create' }
            }
            steps {
                script {
                    gitCheckout(
                        branch: 'main',
                        url: 'https://github.com/anuragjos/mrdevops_java_app.git'
                    )
                }
            }
        }

        stage("Unit Test Maven") {
            when {
                expression { params.action == 'create' }
            }
            steps {
                script {
                    mvnTest()
                }
            }
        }

        stage("Integration Test Maven") {
            when {
                expression { params.action == 'create' }
            }
            steps {
                script {
                    mvnIntegrationTest()
                }
            }
        }

        stage("Static Code Analysis - SonarQube") {
    when {
        expression { params.action == 'create' }
    }
    steps {
        script {
            staticCodeAnalysis('sonarqube-api')
        }
    }
}
    
stage("Quality Gates Analysis - SonarQube") {
    when {expression { params.action == 'create' }}
    steps {
        script {
            QualityGateStatus()
        }
    }
}
    
    }
}
