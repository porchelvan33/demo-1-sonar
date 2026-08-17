pipeline {
    agent any

    stages {
        stage('SCM Checkout') {
            steps {
                echo 'Git Clone'
                git branch: 'main', 
                url: 'https://github.com/porchelvan33/demo-1-sonar.git'
            }
        }
        stage('Code Coverage') {
            steps {
                sh 'echo "This is sonarqube task perfect"'
            }
        }
        stage('Sonarqube Analysis') {
            steps {
                script {
                    def scannerhome = tool name: 'sonar-scanner', type: 'hudson.plugins.sonar.SonarRunnerInstallation'
                    
                withCredentials([string(credentialsId: 'F23', variable: 'SONAR_AUTH_TOKEN')]) {
                    sh """
                            ${scannerhome}/bin/sonar-scanner \
                            -Dsonar.projectKey=porchelvan-23-demo \
                            -Dsonar.sources=app.js \
                            -Dsonar.host.url=http://localhost:9000 \
                             sh "sonar-scanner -Dsonar.login=${SONAR_AUTH_TOKEN}"
                       """
                    }
                
                } 
            }
        }
          
    }
}    
