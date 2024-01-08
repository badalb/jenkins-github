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
              sh 'mvn sonar:sonar -Dsonar.projectKey=jenkins-test -Dsonar.host.url=http://192.168.0.100:9999/'
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
