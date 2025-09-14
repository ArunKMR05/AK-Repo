pipeline {
    agent any

    tools {
        maven 'MAVEN_HOME'   // Jenkins → Manage Jenkins → Global Tool Configuration
        jdk 'JAVA_HOME'     // Set up your JDK here
    }

    // triggers {
    //     githubPush()  // Trigger build on GitHub push
    // }

    stages {
        stage('Checkout Dev Code') {
            steps {
                git branch: 'main', url: 'https://github.com/ArunKMR05/AK-Repo.git'
            }
        }

        stage('Checkout Test Code') {
            steps {
                dir('tests') {
                    git branch: 'main', url: 'https://github.com/ArunKMR05/EclipseRepo.git'
                }
            }
        }

        stage('Run Selenium Tests') {
            steps {
                dir('tests') {
                    bat 'mvn clean test'
                }
            }
        }
    }

    post {
        always {
            junit 'tests/target/surefire-reports/*.xml'
        }
    }
}
