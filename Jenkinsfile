
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

       
stage('Maven Build : mave') {
            steps {
                script {
                    sh 'mvn clean install -DskipTests' 
                }
            }
        }

        

    }
}
