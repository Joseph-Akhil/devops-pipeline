pipeline {
agent any


stages {
stage('Checkout') {
steps {
git url: '/d/DevOps-Lab/central-git/app.git'
}
}


stage('Build Docker Image') {
steps {
sh 'docker build -t devops-app:1.0 .'
}
}


stage('Run Container Test') {
steps {
sh 'docker run -d -p 8081:80 --name test-app devops-app:1.0'
}
}


stage('Cleanup Test Container') {
steps {
sh 'docker rm -f test-app || true'
}
}
}
}
