pipeline {
    agent any

    environment {
        DOCKER_IMAGE = 'raghav2927/medicure-app'
        GENAI_OUTPUT = 'genai_output'
    }

    stages {
        stage('Checkout') {
            steps {
                git 'https://github.com/StarAgileDevOpsTraining/star-agile-health-care.git'
            }
        }

        stage('Build JAR') {
            steps {
                sh 'mvn clean install'
            }
        }

        stage('Analyze Commits with GPT') {
            steps {
                script {
                    def commitLogs = sh(script: "git log -5 --pretty=format:'%h - %s (%an)'", returnStdout: true).trim()
                    echo "Recent Commits:\n${commitLogs}"

                    withCredentials([string(credentialsId: 'openai-api-key', variable: 'API_KEY')]) {
                        def releaseNotes = sh(script: """#!/bin/bash
curl -s https://api.openai.com/v1/chat/completions \\
  -H "Content-Type: application/json" \\
  -H "Authorization: Bearer \$API_KEY" \\
  -d '{
    "model": "gpt-4",
    "messages": [{
      "role": "user",
      "content": "You are a release manager. Based on these recent commits, generate concise, professional release notes in bullet points:\n\n${commitLogs}\n\nOnly output the release notes."
    }],
    "temperature": 0.7
  }' | jq -r '.choices[0].message.content'
""", returnStdout: true).trim()

                        echo "📦 Release Notes by GPT:\n${releaseNotes}"
                    }
                }
            }
        }

        stage('Docker Push') {
            steps {
                withCredentials([usernamePassword(credentialsId: 'docker-hub-creds', usernameVariable: 'USERNAME', passwordVariable: 'PASSWORD')]) {
                    sh '''
                    echo "$PASSWORD" | docker login -u "$USERNAME" --password-stdin
                    docker push $DOCKER_IMAGE
                    '''
                }
            }
        }

        stage('Run Latest Container') {
            steps {
                sh '''
                docker stop medicure-container || true
                docker rm medicure-container || true
                docker run -d --name medicure-container -p 8081:8082 $DOCKER_IMAGE
                '''
            }
        }
    }

    post {
        failure {
            echo '❌ Something went wrong. Check Jenkins logs.'
        }
    }
}