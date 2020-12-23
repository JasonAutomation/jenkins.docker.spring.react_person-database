pipeline {
    agent {
        docker {
            image 'jamesdbloom/docker-java8-maven:latest' 
            args '-v /root/.m2:/root/.m2 -p 8079:8079'
        }
    }
    stages {
        stage('Set Up') {
            steps {
                script {
                    sh 'rm -rf jenkins.docker.spring.react_person-database'
                }
            }
        }
        stage('SCM Checkout') {
            steps {
                sh 'git clone https://github.com/JasonAutomation/jenkins.docker.spring.react_person-database $PWD/jenkins.docker.spring.react_person-database'
            }
        }
        stage('Compile-Package-Test') {
            steps {
                script {
                    dir('$PWD/jenkins.docker.spring.react_person-database') {
                        sh "mvn spring-boot:run"
                    }
                }
            }
        }
    }
