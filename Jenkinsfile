pipeline {
    agent any
    stages {
        stage('Pull Docker Image') {
            steps {
                script {
                    sh 'docker pull urmsandeep/ai-artistic-style-service:latest'
                }
            }
        }
        stage('Run Tests') {
            steps {
                script {
                    sh '''
                    
                    '''
                }
            }
        }
        stage('Deploy Service') {
            steps {
                script {
                    sh '''
                    docker-compose down
                    docker-compose up -d
                    '''
                }
            }
        }
        stage('Verify Deployment') {
            steps {
                script {
                    sh '''
                    sleep 5
                    curl -X POST http://172.22.0.2:5001/styleTransfer -F "image=@image.jpg" --output styled_output.jpg
                    '''
                }
            }
        }
    }
    post {
        always {
            sh 'docker system prune -f'
        }
        success {
            echo 'Pipeline executed successfully!'
        }
        failure {
            echo 'Pipeline failed. Check logs for errors.'
        }
    }
}
