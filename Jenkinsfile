pipeline {
    agent any

    stages {
        stage('Build Docker Image') {
            steps {
                echo 'Building Docker image...'
                sh 'docker build -t devops-app .'
            }
        }

        stage('Run Container Test') {
    steps {
        echo 'Running container test...'
        sh '''
        docker rm -f test-container || true
        docker run -d -p 8081:80 --name test-container devops-app
        '''
    }
}


        stage('Cleanup Test Container') {
            steps {
                echo 'Cleaning up container...'
                sh 'docker rm -f test-container || true'
            }
        }
    }

    post {
        success {
            echo 'Pipeline completed successfully 🎉'
        }
        failure {
            echo 'Pipeline failed ❌'
        }
    }
}
