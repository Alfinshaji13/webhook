pipeline {
    agent any
    tools{
        maven 'maven_3_8_6'
    }
    stages{
        stage('Build Maven'){
            steps{
                checkout([$class: 'GitSCM', branches: [[name: '*/main']], extensions: [], userRemoteConfigs: [[url: 'https://github.com/Java-Techie-jt/devops-automation']]])
                bat 'mvn clean install'
            }
        }
         stage ('Code Quality') {
            steps {
                withSonarQubeEnv('sonarqubeScanner-4.7.0') {
                bat 'mvn -f pom.xml sonar:sonar'
                }
      }
    }
        
    }
}
