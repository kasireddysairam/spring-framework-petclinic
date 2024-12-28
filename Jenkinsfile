
pipeline {
    agent any
    
tools {
        maven 'maven'  
    } 
    environment {
        SCANNER_HOME=tool 'sonarqube_scanner'
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


         
        stage("Sonarqube Analysis "){
            steps{
                withSonarQubeEnv('sonarqube-server') {
                    sh ''' $SCANNER_HOME/bin/sonar-scanner -Dsonar.projectName=Petclinic \
                    -Dsonar.java.binaries=. \
                    -Dsonar.projectKey=Petclinic '''
    
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
