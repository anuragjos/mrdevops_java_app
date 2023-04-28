@Library('my-shared-library') _
pipeline{
    agent any
    stages{
        stage("Git Checkout form SCM"){
            agent{
                docker{
                    image 'maven'
                }
            }
            steps{
                script{
                    gitCheckout(
                        branch: "devops",
                        url: "https://github.com/anuragjos/mrdevops_java_app.git"
                    )
                }
            }
        }
        stage("Unit Test Maven"){
            steps{
                script{
                    mvnTest()
                }
            }
        }
    }
}