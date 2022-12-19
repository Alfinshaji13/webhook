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
                def scannerHome = tool 'sonarqubeScanner-4.7.0';
                withSonarQubeEnv('sonarqube-9.7.1') {
                    bat "${scannerHome}/bin/sonar-scanner"
                    bat 'mvn sonar:sonar'
                }
      }
    }
        
    }
}
