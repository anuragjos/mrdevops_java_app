@Library('my-shared-library') _
pipeline{
    agent any
    parameters{
        choice(name: 'action', choices: 'create\ndelete', description: 'choice create/Destroy')
        string(name: 'ImageName', description: "name of the docker build", defaultValue: 'javaapp')
        string(name: 'ImageTag', description: "tag of the dockerbuild", defaultValue: 'v1')
        string(name: 'AppName', description: "name of the Application", defaultValue: 'springboot')
    }
    stages{
        
        stage("Git Checkout form SCM"){
            when { expression {params.action == 'create'} }
            steps{
//                 agent{
//                 docker{
//                     image 'maven'
//                 }
//             }
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
            when { expression {params.action == 'create'} }
            steps{
                script{
                    def  SonarQubecredentialsId = 'sonarqube-api'
                    staticCodeAnalysis(SonarQubecredentialsId)
                }
            }
        }
        stage("Quality Gate Check Sonar Qube"){
            when { expression {params.action == 'create'} }
            steps{
                script{
                    def  SonarQubecredentialsId = 'sonarqube-api'
                    QualityGateStatus(SonarQubecredentialsId)
                }
            }
        }
        stage("Maven Build"){
            when { expression {params.action == 'create'} }
            steps{
                script{
                    mvnBuild()
                }
            }
        }
        stage("Docker Image Build"){
            when { expression {params.action == 'create'} }
            steps{
                script{
                    dockerBuild("${params.ImageName}","${params.ImageTag}","${params.AppName}")
                }
            }
        }
    }
}
