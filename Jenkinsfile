pipeline {
    agent any

   

    stages {
        stage('Checkout Code from GitHub') {
            steps {
                git branch: 'main', url: 'https://github.com/Suryarv05/pet_shop.git'
            }
        }

        stage('Build with Maven') {
            steps {
                sh 'mvn clean package'
            }
        }

        stage('Deploy to Tomcat') {
            steps {
                deploy adapters: [
                    tomcat9(
                        credentialsId: 'tomcre',
                        path: '',
                        url: 'http://13.202.89.155:8090/'
                    )
                ],
                contextPath: 'bhupesh',
                war: '**/*.war'
            }
        }
    }

    post {
        success {
            echo '✅ Deployment successful!'
        }
        failure {
            echo '❌ Deployment failed. Check the console output for details.'
        }
    }
}
