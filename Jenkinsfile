pipeline {
    agent any

    environment {
        FRONTEND_REPO = "https://github.com/Tejassoni05/frontend-mechyam.git"
        BACKEND_REPO  = "https://github.com/nebulytixtechnologies-web/Mechyam-Backend.git"
    }

    stages {

        stage('Checkout Frontend') {
            steps {
                dir('frontend') {
                    git url: "${FRONTEND_REPO}", branch: 'main'
                }
            }
        }

        stage('Checkout Backend') {
            steps {
                dir('backend') {
                    git url: "${BACKEND_REPO}", branch: 'main'
                }
            }
        }

        stage('Build Backend') {
            steps {
                dir('backend') {
                    sh 'mvn clean package -DskipTests'
                }
            }
        }

        stage('Build Frontend') {
            steps {
                dir('frontend') {
                    sh 'npm install'
                    sh 'npm run build'
                }
            }
        }

        stage('Docker Build') {
            steps {
                sh '''
                docker build -t mechyam-backend ./backend
                docker build -t mechyam-frontend ./frontend
                '''
            }
        }

        stage('Deploy') {
            steps {
                sh '''
                docker rm -f backend frontend || true

                docker run -d -p 8081:8080 --name backend mechyam-backend
                docker run -d -p 80:80 --name frontend mechyam-frontend
                '''
            }
        }
    }

    post {
        success {
            echo "CI/CD Pipeline executed successfully ✅"
        }
        //always {
        //    cleanWs()
        //}
    }
}
