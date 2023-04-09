@Library('my-shared-library') _
pipeline{
    agent any
    tools{
        maven 'maven'
    }
    
    stages{
        stage("Git Checkout SCM"){
            steps{
                script{
                    gitCheckout(
                        branch: "devops",
                        url: "https://github.com/anuragjos/mrdevops_java_app.git"
                    )
                    
                }
            }
        }
        stage("Maven Unit Test"){
            steps{
                script{
                    mvnTest()
                }
            }
        }
    }
}