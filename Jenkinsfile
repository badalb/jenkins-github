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
              sh 'mvn sonar:sonar -Dsonar.projectKey=jenkins -Dsonar.host.url=http://127.0.0.1:8084 -Dsonar.login=3e5a578a8255212ac5c804079806387ed8bfc429'
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
