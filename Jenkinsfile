@Library('app-libs') _
pipeline{
    agent any
    stages{
        stage("Build"){
            steps{
                git credentialsId: '5833e9de-fce4-4476-99a8-0e0ef26e2aa9', url: 'https://github.com/javahometech/my-app'
            }
    }
    stage("maven test"){
            steps{
                sh 'mvn clean package'
                sh 'mv target/myweb*.war target/myweb.war'
            }
    }
    stage("deployment"){
            steps{
                sshagent(['tomcat']) {
                 sh "scp -o StrictHostKeyChecking=no target/myweb*.war ec2-user@172.31.22.129:/opt/tomcat8/webapps"
                 sh "ssh ec2-user@172.31.22.129 /opt/tomcat8/bin/shutdown.sh"
                 sh "ssh ec2-user@172.31.22.129 /opt/tomcat8/bin/startup.sh"
              }
            }
    }
}
}
