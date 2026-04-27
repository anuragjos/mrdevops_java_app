@Library('my_shared_libraries') _

pipeline {
    agent any

    tools {
        maven 'maven'
    }

    stages {
        stage("Git Checkout") {
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
            steps {
                script {
                    mvnTest()
                }
            }
        }

        stage("Integration Test Maven") {
            steps {
                script {
                    mvnIntegrationTest()
                }
            }
        }
    }
}

