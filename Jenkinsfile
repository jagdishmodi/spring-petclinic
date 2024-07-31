#!groovy
pipeline {
    agent none
   stages {     
    stage('Maven Install') {
      agent {         
        docker {          
         image 'maven:3.8.6'         
     }       
  }       
  steps {
       sh 'mvn clean install'
       }
 }
    stage('SonarQube Analysis') {
            steps {
                withSonarQubeEnv('ServerNameSonar') {
                    bat '''mvn clean verify sonar:sonar -Dsonar.projectKey=ProjectNameSonar -Dsonar.projectName=spring -Dsonar.host.url=http://localhost:9000''' //port 9000 is default for sonar
                    echo 'SonarQube Analysis Completed'
                }
            }
        }
     }
   }

