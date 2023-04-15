@Library('my-shared-library') _
pipeline{
 agent any
  tools {
        maven 'Maven 3.6.3'
  }
    stages{
         stage("Git checkout form SCM"){
            steps{
                script{
                    gitCheckout(
                        branch: "devops",
                        url: "https://github.com/anuragjos/mrdevops_java_app.git"
                    )

                }

            }
        }
        stage("Maven Unit Testing"){
            steps{
                script{
                    mvnTest()
                }
            }
        }
    }
}