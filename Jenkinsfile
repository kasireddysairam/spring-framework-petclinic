
pipeline {
    agent any
    
tools {
        maven 'maven'  
    }
    
    stages {
        stage('git checkout ') {
            steps {
                git branch: 'main', url: 'https://github.com/kasireddysairam/spring-framework-petclinic.git'
            }
        }

        stage('mvn compile') {
            steps {
                script {
                    // Run Maven or Gradle build
                    sh 'mvn  compile'
                }
            }
        }
        

        stage('Unit Test maven') {
            steps {
                script {
                    // Run Maven or Gradle build
                    sh 'mvn   test'
                }
            }
        }


         stage('Static code analysis: Sonarqube') {
            steps {
               
                   withSonarQubeEnv(credentialsId: 'sonarqube-token') {
                   sh 'mvn clean package sonar:sonar'
                }
            }
        }

     

stage('Maven Build : mave') {
            steps {
                script {
                    sh 'mvn clean install -DskipTests' 
                }
            }
        }

        

    }
}
