pipeline {
  agent any

  tools {
    maven 'maven-3.9.6'
  }
  stages {

   stage('Test') {
      steps {
        sh 'mvn test'
      }
    }


   stage('SonarQube Analysis') {
            steps {
            withSonarQubeEnv("sonarqube-10.3"){
              sh 'mvn sonar:sonar'
            }
              }
        }
      
    stage('Build') {
      steps {
        sh 'mvn clean install -Dmaven.test.skip=true'
      }
    }
      
    stage('Deploy') {
      steps {
        echo 'Deploying....'
      }
    }
  }
}
