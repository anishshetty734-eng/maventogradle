pipeline {
    agent any

    tools {
        maven 'Maven'
        gradle 'Gradle'
        jdk 'JDK'
    }

    stages {

        stage('Checkout') {
            steps {
                git branch: 'master', url: 'https://github.com/anishshetty734-eng/maventogradle'
            }
        }

        stage('Build') {
            steps {
                dir('mymvntogrdl') {   // ✅ FIX
                    sh 'mvn clean package'
                }
            }
        }

        stage('migrate') {
            steps {
                dir('mymvntogrdl') {   // ✅ FIX
                    sh 'gradle init --type pom'
                }
            }
        }

    }

    post {
        success {
            echo 'Build and deployment successful!'
        }
        failure {
            echo 'Build failed!'
        }
    }
}
