pipeline {
    agent any
    tools {
        maven 'maven363'
    }
    stages {
        stage( 'sonnar' ){
            steps{
              withSonarQubeEnv('sonar-6') {
                echo 'SCAN SONNAR'
                sh 'mvn clean package sonar:sonar'
              }
           }
        }
    stage( 'Deployment' ){
            steps{
                deploy adapters:[tomcat8(credentialsId:'TomcatCreds', path:'',url:'http://tajri:8888/')], contextPath:'test',war:'target/*.war'
              }
           }
        }
}
