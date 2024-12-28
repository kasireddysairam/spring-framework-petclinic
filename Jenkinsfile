
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

       stage('SonarQube Analysis') {
    steps {
        withSonarQubeEnv(
            'sonar.projectKey': 'petclinic', 
            'sonar.projectName': 'petclinic', 
            'sonar.projectVersion': '1.0', 
            'sonar.sources': 'src/main/java,src/main/resources', 
            'sonar.java.binaries': 'target/classes' 
        ) {
            sh 'mvn sonar:sonar' 
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
