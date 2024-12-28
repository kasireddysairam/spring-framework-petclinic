
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
            'sonar.projectKey': 'petclinic', // Replace with your project key
            'sonar.projectName': 'petclinic', // Replace with your project name
            'sonar.projectVersion': '1.0', // Replace with your project version
            'sonar.sources': 'src/main/java,src/main/resources', // Comma-separated source directories
            'sonar.java.binaries': 'target/classes' // Path to compiled classes
        ) {
            sh 'mvn sonar:sonar' // Assuming Maven is used for building
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
