#!groovy
pipeline {
    agent {
        label env.DEFAULT_JENKINS_AGENT
    }
    environment {
        APPSCAN_KEY_SECRET = credentials('appscan-key-secret')
        APPSCAN_KEY_ID = credentials('appscan-key-id')
    }
    stages {
        stage('Scan') {
            steps {
                checkout scm: [$class: 'GitSCM', branches: [[name: '*/demo']], userRemoteConfigs: [[ url: 'git@github.com:devops-insights/Microservices_CatalogAPI.git']]]
            
                sh '''
                    #!/bin/bash +x
                    chmod +x ./static_scan.sh

                    ./static_scan.sh
                '''
            }
        }

    }
}
