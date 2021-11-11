pipeline{
    agent any
    triggers {
      pollSCM '* * * * *'
    }
    stages{
        stage("SCM"){
            steps{
               echo "job ran.....again and again"
            }
        }
        stage("QA"){
            steps{
               echo "ran QA.....again and again"
            }
        }
        stage("Production"){
            steps{
               echo "Production"
            }
        }
    }
}
