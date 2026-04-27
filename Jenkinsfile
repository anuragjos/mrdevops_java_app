@Library('my_shared_libraries') _

pipeline {
    agent any

    tools {
        maven 'maven'
    }

    stages {
        stage("Git Checkout") {
            steps {
                gitCheckout(
                    branch: 'main',
                    url: 'https://github.com/anuragjos/mrdevops_java_app.git'
                )
            }
        }

        stage("Unit Test Maven") {
            steps {
                script {
                    mvnTest()
                }
            }
        }
    }
    stage(" Maven integration test") {
            steps {
                script {
                    mvnIntegrationTest()
                }
            }
        }
}

