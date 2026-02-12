pipeline {
    agent any

    stages {
        stage('Checkout Code') {
            steps {
                echo "Cloning repository..."
                checkout scm
            }
        }

        stage('Verify') {
            steps {
                echo "Repository cloned successfully!"
                sh 'ls -la'
            }
        }
stage('Install Dependencies') {
    steps {
        echo "Installing dependencies..."
        sh 'npm install'
    }
}

stage('SonarCloud Analysis') {
    environment {
        SONAR_TOKEN = credentials('sonarcloud-token')
    }
    steps {
        script {
            def scannerHome = tool 'sonar-scanner'
            sh """
            ${scannerHome}/bin/sonar-scanner \
              -Dsonar.projectKey=sunila-k05_Zomato-Application-Secure-Deployment-with-Dev-Sec-Ops-CI-CD \
              -Dsonar.organization=sunila-k05 \
              -Dsonar.host.url=https://sonarcloud.io \
              -Dsonar.sources=src \
              -Dsonar.exclusions=node_modules/** \
              -Dsonar.c.file.suffixes=- \
              -Dsonar.cpp.file.suffixes=- \
              -Dsonar.objc.file.suffixes=- \
              -Dsonar.token=${SONAR_TOKEN}
            """
        }
    }
}




 }
}
