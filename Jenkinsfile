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
                withSonarQubeEnv('sonarqube-9.7.1') {
                    bat 'mvn clean verify sonar:sonar \
                        -Dsonar.projectKey=efg \
                        -Dsonar.host.url=http://localhost:9000 \
                        -Dsonar.login=sqp_3e6c773ffac6192cd25e1f431f8c9764eb66cec1'
                }
      }
    }
        
    }
}
