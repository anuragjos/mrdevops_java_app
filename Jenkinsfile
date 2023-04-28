pipeline{
    agent any
    stages{
        stage("Git Checkout form SCM"){
            steps{
                script{
                    git branch: 'devops', url: 'https://github.com/anuragjos/mrdevops_java_app.git'
                }
            }
        }
    }
}