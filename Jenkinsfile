
pipeline {
    agent any

    stages {
        stage('git checkout ') {
            steps {
                git branch: 'main', url: 'https://github.com/kasireddysairam/spring-framework-petclinic.git'
            }
        }

        stage('Build') {
            steps {
                script {
                    // Run Maven or Gradle build
                    sh 'mvn clean install -DskipTests'
                }
            }
        }

    }
}
