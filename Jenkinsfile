@Library('my-shared-library') _
pipeline{
    agent any
    parameters{
        choice(name: 'action', choices: 'create\ndelete', description: 'choice create\Destroy')
    }
    stages{
        
        stage("Git Checkout form SCM"){
            when { expression {params.action == 'create'} }
            steps{
                agent{
                docker{
                    image 'maven'
                }
            }
                script{
                    gitCheckout(
                        branch: "devops",
                        url: "https://github.com/anuragjos/mrdevops_java_app.git"
                    )
                }
            }
        }
        stage("Unit Test Maven"){
            when { expression {params.action == 'create'} }
            steps{
                script{
                    mvnTest()
                }
            }
        }
        stage("Maven Integration Testing"){
            when { expression {params.action == 'create'} }
            steps{
                script{
                    mvnIntegrationTest()
                }
            }
        }
        stage("Static Code Analysis Sonar Qube"){
            steps{
                script{
                    def  SonarQubecredentialsId = 'sonarqube-api'
                    staticCodeAnalysis(SonarQubecredentialsId)
                }
            }
        }
    }
}