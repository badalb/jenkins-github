pipeline {
  agent any
  environment {
    CI = true
    ARTIFACTORY_ACCESS_TOKEN = credentials('artifactory-access-token')
  }
  tools {
    maven 'maven-3.9.6'
    jfrog 'jfrog'
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
     // stage('Install JFrog CLI') {
     //        steps {
     //            script {
     //                tool 'jfrog'
     //            }
     //        }
     //    }

    stage('Upload to Artifactory') {
      steps {
        //sh 'jf rt upload --url http://192.168.0.100:8882/artifactory/ --access-token ${ARTIFACTORY_ACCESS_TOKEN} target/*.jar factorian/'
        jf 'rt u target/*.jar factorian/'
      }
    }
  
      
    stage('Deploy') {
      steps {
        echo 'Deploying....'
      }
    }
  }
}
