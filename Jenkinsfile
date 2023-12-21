pipeline {
agent any
    
  tools {
    maven 'maven-3.9.6' 
  }
  stages {
    stage ('Build') {
      steps {
        sh 'mvn clean package'
      }
    }
        stage('Deploy') {
            steps {
                echo 'Deploying....'
            }
        }
    }
}
