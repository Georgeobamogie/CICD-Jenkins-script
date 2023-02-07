pipeline {
    agent {
        kubernetes {
            label 'jenkins-agent'
        }
    }
    stages {
        stage('Build') {
            steps {
                sh 'mvn clean package'
            }
        }
        stage('Test') {
            steps {
                sh 'mvn test'
            }
        }
        stage('Upload to Nexus') {
            steps {
                sh 'mvn deploy -DnexusUrl=<NEXUS_URL> -DrepositoryId=<REPOSITORY_ID>'
            }
        }
        stage('Deploy to Development') {
            steps {
                sh 'kubectl apply -f deployment/development.yml'
            }
        }
        stage('Deploy to Production') {
            steps {
                input 'Are you sure you want to deploy to production?'
                sh 'kubectl apply -f deployment/production.yml'
            }
        }
    }
}
